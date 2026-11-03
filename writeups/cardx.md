# CardX — computer vision for trading cards, with a grader that can say "not sure"

A five-part ecosystem that takes trading cards from grid photos to verified eBay listings with **no per-card AI cost** — everything runs locally. Built for the Aegis Card Emporium store.

**My role:** owner, designer, acceptance authority. Implementation was directed across several AI coding agents (Claude lead, GPT/Codex, DeepSeek, Atlas); every stage below carries the measurements from its own record.

## The parts
- **CardSplitter** (PC + Android): grid photos (4×4 mat, flip-in-spot, backs) → straightened, upright, paired front/back JPEGs + a JSON batch manifest. Mat-surface modelling and OCR orientation voting. Golden parity **281/281 slots** against the reference implementation — parity proves the port; on real photos the detector finds 478 of 493. **79 app tests.** The current Android build is desktop-tested; an earlier version was phone-tested.
- **CardIdentify**: fully local identification — DINOv2-small ONNX embeddings + OCR over a **20,670-card / 176-set** Pokémon catalog.
- **CardList**: eBay listing layer. Automated publishing is designed, not built — listings so far are supervised pilots (5 published, 6 drafts saved, duplicate-checked against the live store), run under read-back verification because the pilots produced a failure catalogue (a photo upload silently changed a Finish value; promo defaults had to be caught and reset).
- **Storage & retrieval**: franchise → tier → set → number addressing, lifetime stock IDs kept separate from capture keys, quarantine and PARK cells. (Two conflicting specs existed; the canonical version was chosen by ruling, with three features grafted — neither spec was silently merged.)
- **Robotic put-away (design package)**: a Cartesian gantry design ($392.94 lean BOM, ±1.7 mm, ~3 cards/min). Its independent verifier overturned the lead's vacuum gripper — **17.3 N on a sealed card is a crease risk** — and corrected the ROI (break-even ≈ 8,600 cards). Next step is a bench suction test with a 200-pick go/no-go.

## The decision rule
A "sure" identification requires a **margin over the next *different* card**, not a high raw score — and "sure" is never treated as a calibrated probability.

- Measured: **0 wrong "sure" answers across 294 card fronts**
- The statistical bar, set properly: a Wilson 95% bound under 1% wrong needs **≈381 clean sures** (≈765 for 0.5%)
- Test set frozen and hash-locked; predictions written **before** scoring

The W1–W9 research programme attacked the system's own weaknesses: 885 same-art reprint twins (4.5% of the catalog) that break naive margin tests, stamped variants missing from the catalog, finish recognition from flat photos (a flash/no-flash pair is the designed lever), and small vision-language models measured and **rejected** — they scored 0–2 of 24 and abstained 0 times in 120 tries. That record is why the "not sure" answer matters in this system.

## Code samples

The samples below were written for this page to show how the ideas work. They are simplified, renamed, and use made-up data — they are not the production code, and anything operational (keys, endpoints, catalog data, store details) is left out by design.

**The "sure" rule** — a match counts only if it beats the best *different* card by a margin:

```python
def decide(candidates, margin=0.06):
    # candidates: [(card_id, score), ...] sorted best-first, scores in [0, 1]
    if not candidates:
        return ("not_sure", None)
    best_id, best = candidates[0]
    rival = next((s for cid, s in candidates[1:] if cid != best_id), 0.0)
    if best - rival >= margin:
        return ("sure", best_id)
    return ("not_sure", None)   # a person looks at this one
```

**How many clean "sure" answers prove the error rate?** — the Wilson bound the project uses to set its own bar:

```python
import math

def wilson_upper(errors, n, z=1.96):
    if n == 0:
        return 1.0
    p = errors / n
    denom = 1 + z**2 / n
    centre = p + z**2 / (2 * n)
    spread = z * math.sqrt(p * (1 - p) / n + z**2 / (4 * n**2))
    return (centre + spread) / denom

# 0 errors: n=294 -> upper bound ~1.3% | n=381 -> ~1.0% | n=765 -> ~0.5%
```

**A batch manifest fragment** — what one split photo produces, so every later step can be checked against it:

```json
{
  "batch": "EXAMPLE-0001",
  "photo": "grid_a.jpg",
  "slots": [
    {"slot": 1, "front": "img_001_f.jpg", "back": "img_001_b.jpg",
     "orientation": "ocr-vote", "detector": "found"}
  ]
}
```
