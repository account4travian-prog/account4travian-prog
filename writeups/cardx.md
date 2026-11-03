# CardX: computer vision for trading cards, with a grader that can say "not sure"

CardX takes trading cards from grid photos to eBay listings with no per-card AI cost. The identification runs locally for the Aegis Card Emporium store.

**My role:** owner, designer, acceptance authority. Implementation was directed across several AI coding agents (Claude lead, GPT/Codex, DeepSeek, Atlas).

## What counts as a sure identification

A "sure" identification requires a **margin over the next different card**, not a high raw score. "Sure" is not a calibrated probability.

- Measured: **0 wrong "sure" answers across 294 card fronts**
- The goal the project verifies itself against: enough clean sures for a Wilson 95% bound under 1%, which takes **≈381** (≈765 for 0.5%)
- Test set frozen and hash-locked; predictions written **before** scoring

The W1 to W9 research program tested the system's own weaknesses. It found 885 cards (4.5% of the catalog) with a same-art reprint twin that breaks a naive margin test. Stamped variants missing from the catalog came back "sure" as the plain version. Flat photos settled only 1 of 6 pilot cards on finish; the designed fix is a flash/no-flash pair. Small vision-language models were measured and **rejected**: 0 to 2 of 24 on hard reads, 0 abstentions in 120 tries.

## The parts

- **CardSplitter** (PC + Android) turns grid photos (4×4 mat, flip-in-spot, backs) into straightened, upright, paired front/back JPEGs plus a JSON batch manifest. Mat-surface modeling and OCR orientation voting. Golden parity against the reference implementation: 64/64 photos and 281/281 slots. Parity proves the port, not that each crop is right. On 493 real photos the detector finds 478. The app is at v0.2.4 with 79 passing tests; only v0.1 has run on a real phone.
- **CardIdentify** identifies cards fully locally: DINOv2-small ONNX embeddings plus OCR over a **20,670-card / 176-set** Pokémon catalog.
- **CardList** is the eBay listing layer. Automated publishing is designed, not built. The listings are supervised pilots: 5 published, 6 drafts saved, duplicate-checked against the store's active singles under read-back verification. The pilots produced a failure catalog: a photo upload silently changed a Finish value, and promo defaults had to be caught and reset.
- **Storage and retrieval**: franchise, tier, set, and number addressing, lifetime stock IDs kept separate from capture keys, and quarantine and PARK cells. Two conflicting specs existed; a ruling of 2026-10-28 chose one as canonical and grafted three features from the other, and neither was silently merged.
- **Robotic put-away** is a design package: a Cartesian gantry ($392.94 lean BOM, ±1.7 mm, about 2.97 cards/min). Its independent verifier corrected the lead's vacuum scheme (17.3 N on a sealed card is a crease risk) and corrected the ROI to break even near 8,600 cards. Next is a bench suction test with a 200-pick go/no-go.

## Code samples

An agent wrote the samples below to show how the rules work. They are simplified, renamed, and use made-up data. They are not production code; anything operational (keys, endpoints, catalog data, store details) is left out.

**The "sure" rule.** A match counts only if it beats the best *different* card by a margin:

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

**How many clean "sure" answers prove the error rate?** The Wilson bound the project uses to set its own bar:

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

**A batch manifest fragment.** What one split photo produces, so every later step can be checked against it:

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
