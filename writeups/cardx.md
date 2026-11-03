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
