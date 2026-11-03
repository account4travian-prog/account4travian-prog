# The Reader + publishing system

[reader.wardenlog.org](https://reader.wardenlog.org) is the public home for my published fiction: 15 Ghost Weights chapters and Glyphbound chapters 1-5, both through the chapter pipeline, and A Work of Magic chapters 1-9 (AI-completion drafts, AI work disclosed) from the private WriteProject project. It also hosts the five-Muse pipeline guide.

**How a release is checked**
- Acceptance is hash-bound: my verdict binds the chapter and its exact text SHA-256. Any later edit voids the acceptance and requires a fresh verdict.
- The released text is checked after publication on the reader, Royal Road, and Wattpad. Glyphbound chapters 1-5 were verified on all three.
- Rejected text is never pulled. It stays public until an accepted fix swaps in.

**Why that rule exists**
Chapter 13 passed the full gauntlet, I accepted it on 2026-10-14, and it published. My full read that evening reversed the verdict with 22 notes. I ruled that the text stays public until an accepted fix swaps in. The accepted revision replaced it on all three platforms with the swap verified 39/39. The post-mortem is in the [chapter pipeline](https://github.com/account4travian-prog/chapter-pipeline) README.

**My role:** publication authority. Nothing goes public without my explicit word, chapter by chapter. The system exists to prove that what the public reads is byte-for-byte what I accepted.
