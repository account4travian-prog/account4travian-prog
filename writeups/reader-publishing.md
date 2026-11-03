# The Reader + publishing system

[reader.wardenlog.org](https://reader.wardenlog.org) is the public home for the published fiction produced through the chapter pipeline: Ghost Weights, Glyphbound, and A Work of Magic, plus the five-Muse pipeline guide.

**The engineering point is verification, not hosting**
- Every release is hash-verified: the text accepted by Jordan is bound to its exact SHA, and what renders on the reader (and on Royal Road and Wattpad) is checked against that hash after publication.
- A chapter's acceptance is hash-bound, any post-acceptance edit invalidates the acceptance and requires a fresh verdict.
- Rejected text is never pulled silently; it stays live until an accepted fix swaps in.

**Jordan's role:** publication authority. Nothing goes public without his explicit word, chapter by chapter; the system exists to prove that what the public reads is byte-for-byte what he accepted.
