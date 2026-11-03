# The Office: a multi-agent workspace with evaluator separation

A persistent workplace where my agents hold roles, do work, and review each other. One rule, written on 2026-10-31 before any build: no agent grades its own work.

**The rule**
Where an agent is graded, that agent is not the writer, not the scorer, and not the host of the vault it is tested against. Scores are hash-committed before the graded agent sees them, and it gets pass/fail plus a category, never the grader's detail.

The rule exists because the first design failed it by construction: the auditor's first finding was that Atlas sat as employee, writer, scorer, and vault host at once.

**The two reviews**
Two independent reviews ran against the design: an auditor's 14 findings and an adversarial review's 19 attacks and 14 gaps. Every finding was dispositioned on the record; all but one was accepted. The rejection is kept with its reason: the review prescribed no desk for the auditor, and I ruled that the auditor's own choice governs the auditor's setup.

**The verification record**
Wave 3 failed its first cold verification with seven findings, was fixed, and passed 484/484. The Wave 4 cutover (2026-11-01) made the hub the system of record, gated on a 24-hour chaos test, mirror parity (7 of 7), and a restore drill; the suite was at 235/235 at that cutover. Two defects stay open on the record: a ticker freeze never root-caused, and a failed resource audit.

**My role:** owner and acceptance authority. I set the rule and dispositioned the findings. I directed the implementation across the agents who work in it.

The Office is private.
