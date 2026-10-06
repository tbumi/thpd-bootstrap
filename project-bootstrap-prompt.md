# Project Bootstrap

I want to start a new software project using an agent-driven development
workflow.

Your job in this session is to establish the product requirements, initial
architecture, engineering conventions, and documentation that future coding
agents will use as the source of truth.

**Do not implement the application or product features during this session.**

## Working approach

Start by inspecting the existing repository, if one exists. Briefly summarize
what already exists, including relevant code, documentation, conventions, and
constraints. If there is no repository, establish the intended project location
and context with me.

Then conduct the structured requirements interview below. Do not assume
requirements I have not given you. Clearly distinguish my stated requirements
from your recommendations and any assumptions that need confirmation.

Interview me conversationally in small, coherent groups of questions. Do not
dump dozens of questions at once. Drill deeper when an answer exposes an
important decision. Challenge requirements or technology choices when you
identify a meaningful problem or simpler alternative, explaining the trade-offs.

Do not silently make major architectural decisions. Discuss them with me first.
Use the repository and this interview as context; the resulting documentation
must be understandable without access to our chat history.

## Structured requirements interview

### Phase 1: Discovery

Maintain a checklist throughout the interview and work through all 20 areas:

1. Product purpose and problem statement
2. Target users and user types
3. Primary user journeys
4. MVP scope
5. Explicit non-goals and out-of-scope functionality
6. Platforms and deployment targets
7. UI/UX expectations
8. Data model and persistence
9. Authentication and authorization
10. External services and integrations
11. Security, privacy, and sensitive data
12. Performance and scalability expectations
13. Offline, synchronization, and concurrency behavior where applicable
14. Error handling and important failure scenarios
15. Testing strategy
16. Observability and diagnostics
17. Deployment and CI/CD
18. Technical constraints
19. Preferred technologies
20. Known risks, unknowns, and important trade-offs

Not every area will apply. Mark an area `N/A` only after explicitly establishing
that it does not apply.

### Phase 2: Gap analysis

After every area has been discussed or explicitly marked `N/A`, classify each
as:

- **RESOLVED**: Sufficient information exists to document the project.
- **N/A**: Confirmed not applicable.
- **OPEN**: An unresolved question could materially affect product behavior,
  architecture, security, data design, or MVP scope.
- **DEFERRED**: We have explicitly agreed that the decision can safely be made
  later.

Do not classify missing information as `DEFERRED` without an explicit agreement.

Present a gap-analysis summary containing:

- Your current understanding of the product
- Proposed MVP boundaries and primary user journeys
- Proposed initial architecture, major entities and relationships, and external
  system boundaries
- Important assumptions and security-sensitive behavior
- The status of every interview area
- All `OPEN` and explicitly `DEFERRED` items
- Major trade-offs and risks

Ask me to correct anything that is wrong or incomplete. Resolve `OPEN` items
through further discovery and update the summary as needed.

### Phase 3: Explicit confirmation

The interview may end only when all of these conditions are true:

- Every interview area is `RESOLVED`, `N/A`, or explicitly `DEFERRED`.
- There are no `OPEN` items.
- The MVP boundary and primary user journeys are defined.
- Major entities and their relationships are understood.
- External system boundaries are understood.
- Security-sensitive behavior has been identified.
- The initial architecture can be explained without unstated assumptions.
- Major architectural choices have been agreed or explicitly deferred.
- Acceptance criteria can be written for the MVP requirements.
- I have reviewed the final gap-analysis summary.
- I explicitly confirm that the requirements interview is complete.

**Ask for this confirmation explicitly. Do not infer it from the conversation.**

If I do not confirm, return to Discovery or Gap Analysis as appropriate. Only
after I explicitly confirm completion may you generate or finalize the project
documentation.

## Documentation pass

After confirmation, propose an appropriate documentation structure and create or
update the useful documents based on our agreed requirements and decisions.
Consider the following structure, but do not create documents merely to fill it:

| Path                                      | Purpose                                                    |
| ----------------------------------------- | ---------------------------------------------------------- |
| `README.md`                               | What the project is and how to run it                      |
| `AGENTS.md`                               | How coding agents should work in this repository           |
| `docs/product/vision.md`                  | What we are building and why                               |
| `docs/product/requirements.md`            | Required product behavior and acceptance criteria          |
| `docs/architecture/overview.md`           | System structure and architectural boundaries              |
| `docs/architecture/decisions/nnn-slug.md` | Reasons for significant technical decisions                |
| `docs/design/`                            | UI/UX guidance, including a design system when appropriate |
| `docs/plans/`                             | Plans for substantial features or changes                  |

For ADR filenames, use a zero-padded incrementing number for `nnn` and a short
kebab-cased summary for `slug`.

### Product documentation

Capture the product purpose, target users, goals, non-goals, MVP boundaries,
major user journeys, functional and non-functional requirements, constraints,
and assumptions. Record explicitly deferred decisions so future agents can see
what remains undecided.

Give important requirements stable identifiers such as `R-001`. Make
requirements testable and include acceptance criteria wherever practical.

### Architecture and decision records

Document the agreed initial architecture and the reasoning behind it. For
significant technical decisions, create Architecture Decision Records
containing:

- Context
- Considered options
- Decision
- Rationale
- Consequences and trade-offs

Represent deferred choices as deferred; do not present them as agreed decisions.

### Agent operating instructions

Create a concise, actionable `AGENTS.md` that explains:

- Which project documents agents must read before making changes
- Repository structure and architectural boundaries
- Coding conventions and dependency policy
- Testing and documentation expectations
- Commands for build, test, lint, and type-check
- Rules for migrations, APIs, security, and secrets where applicable
- The development workflow and definition of done

Document commands accurately. If tooling is not yet established, make that
status explicit rather than presenting unverified commands as working.

The longer the document is, the less reliable an agent will follow it, so keep
it short. A useful filter is: "If this sentence is removed, would it cause
errors?"

## Development workflow and source of truth

Design the repository around this workflow:

**requirement → implementation plan → implementation → tests → verification →
documentation**

Store feature implementation plans under `docs/plans/` when the work is
substantial enough to benefit from a plan. Document this workflow now; feature
implementation belongs in later sessions.

Permanent documentation should describe the current system, agreed product and
architecture, and important historical decisions. Clearly distinguish proposed
architecture from an existing implementation. Avoid filling permanent documents
with temporary implementation details.

The repository should eventually contain enough context that a fresh
coding-agent session can understand the project without relying on previous chat
history. Important decisions made during this conversation must therefore be
captured in the appropriate project documentation rather than existing only in
our conversation.

If documentation and implementation disagree, surface the discrepancy explicitly
rather than silently choosing one.

## Final consistency check and handoff

Before finishing, check the generated documents for consistency and report:

- Contradictions found and resolved
- Remaining explicitly deferred decisions
- Assumptions recorded in the documentation
- ADRs created
- Whether the repository is ready for the first feature-planning session, and
  any remaining blockers

The session should leave the repository with a clearly defined product,
documented MVP scope and requirements, an agreed initial architecture, recorded
major architectural decisions, clear engineering conventions, an effective
`AGENTS.md`, and a documented workflow for future agent sessions.

Begin now by examining the repository if applicable, briefly explaining what
already exists, and asking the most important initial product questions.
