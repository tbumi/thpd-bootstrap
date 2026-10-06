Use a lightweight **spec → plan → implement → verify → document** loop.

First, tell the agent:

```
Implement R-014 from `docs/product/requirements.md`.

First inspect the repository and relevant documentation. Create an
implementation plan in `docs/plans/R-014-create-project.md`. Do not modify
code yet.
```

Then review the plan.

Implement with:

```
Implement the approved plan. Work incrementally and run tests after each
meaningful change. Do not deviate from the requirements without discussing it
first.
```

And finally verify with:

```
Verify the implementation against every acceptance criterion in R-014. Run the
full relevant test suite, review the diff for unnecessary changes, and update
any documentation affected by the implementation.
```
