# The Office — a multi-agent workspace with evaluator separation

A persistent workplace where several AI agents hold roles, do work, and review each other — with one blocking design rule: **no agent grades its own work.** Evaluator role separation is enforced structurally, not by convention.

**How the rule was earned**
- Two independent adversarial reviews (an outside auditor's 14 findings; a second reviewer's 19 attacks / 14 gaps) were run against the design; 47 of 48 findings were accepted and implemented.
- A 24-hour chaos test passed; the test suite stands at 235/235.
- The shared hub became the system of record in a Wave 4 cutover (2026-11-01), with mirror parity and a restore drill verified green.

**Status:** in progress and currently paused at Jordan's direction, checkpointed after a terminal overhaul. The system is private; this write-up is its public record.

**Jordan's role:** owner and acceptance authority — he set the role-separation rule, dispositioned the review findings, and ordered the pause. Implementation was directed across the agents who also work in it.
