# War room skills

A Claude skill I built that runs a simulated cross-functional design review. Five seats—product management, engineering, content design, product design, and the user—each critique the same artifact from their own rubric. Then the skill surfaces where they disagree.

The value isn't five opinions. It's the collisions between them.

**[Install it from GitHub →](https://github.com/mitchellalicht/war-room-review)**

## How it works

1. **Get context first.** What is it, what stage, what constraints, and where I'm unsure. A rough concept and a pre-ship candidate get different reviews.
2. **Each seat writes independently.** Notes are written from that discipline's rubric before any seat reads the others', so the voices don't collapse into one.
3. **Every note carries a severity.** Blocking, should fix, or consider. Each seat gives 2–4 notes, or says "no blocking concerns" and stops.
4. **Then the tensions.** The output ends with where the seats disagree, what's underneath each disagreement, and who should own the decision.

A review where all five agree counts as a failed review.

## The five seats

| Seat | Accountable for |
| --- | --- |
| **Product management** | Whether it's worth building and moves a number |
| **Engineering** | Whether it can be built, at what cost, and how it breaks |
| **Content design** | Whether the words let someone understand what's happening and what to do next |
| **Product design** | Whether it works as an interface and belongs to the same product |
| **The user** | Whether a real person can finish the task, including with assistive tech |

## Three modes

- **Full review** — all five seats, the tensions, and the top three fixes
- **Scoped review** — only the seats you name, plus the tensions between them
- **Re-review** — come back with a revised artifact and each earlier tension is marked resolved, moved, untouched, or disputed

## What good disagreement looks like

> **Eng wants the error state simplified; content design wants the specific message.** Eng's point is that six error variants means six strings to maintain and translate for an edge case hit by under 1% of users. Content's point is that "Something went wrong" is the reason those users file tickets. Underlying question: is the support cost of the generic message higher than the maintenance cost of the specific ones? Someone should check the ticket volume—this is answerable, not a matter of taste.

Each tension is labeled as answerable (check the data), a real tradeoff (name who decides), or a false conflict (one small change satisfies both).
