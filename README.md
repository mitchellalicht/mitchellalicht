# War room skills

A Claude skill I built that runs a simulated cross-functional design review. Four disciplines—product management, engineering, content design, and product design—each critique the same artifact from their own rubric. Then the skill surfaces where they disagree.

The value isn't four opinions. It's the collisions between them.

## How it works

1. **Get context first.** What is it, what stage, what constraints, and where I'm unsure. A rough concept and a pre-ship candidate get different reviews.
2. **Each reviewer writes independently.** Notes are written from that discipline's rubric before anyone sees the others', so the four voices don't collapse into one.
3. **Every note carries a severity.** Blocking, should fix, or consider. Each discipline gives 2–4 notes, or says "no blocking concerns" and stops.
4. **Then the tensions.** The output ends with where the disciplines disagree, what's underneath each disagreement, and who should own the decision.

A review where all four agree counts as a failed review.

## The four reviewers

| Discipline | Accountable for | Signature questions |
| --- | --- | --- |
| **Product management** | Whether it's worth building and moves a number | Which problem does this solve? What's the success metric? What's the smallest version that tests the hypothesis? What happens if we don't build it? |
| **Engineering** | Whether it can be built, at what cost, and how it breaks | Where are the missing states? What's the data actually like? Does this exist already? What's the maintenance tail? |
| **Content design** | Whether the words let someone understand what's happening and what to do next | Does the language match the user's model or the system's? Is this term consistent across the flow? What does the button promise? Is copy patching a structural problem? |
| **Product design** | Whether it works as an interface and belongs to the same product | What's the one thing on this screen? Is this the system's pattern or a new one? Does it survive the longest string and the densest data? |

## Output format

```
## Context
## Product management
## Engineering
## Content design
## Product design
## Where they disagree
## If you fix three things
```

## What good disagreement looks like

> **Eng wants the error state simplified; content design wants the specific message.** Eng's point is that six error variants means six strings to maintain and translate for an edge case hit by under 1% of users. Content's point is that "Something went wrong" is the reason those users file tickets. Underlying question: is the support cost of the generic message higher than the maintenance cost of the specific ones? Someone should check the ticket volume—this is answerable, not a matter of taste.

Each tension states both positions in their strongest form, names the real question underneath, and points at what would resolve it. When it's a true tradeoff, it names who should decide.

## Design principles

- **Disagreement is the product.** Diplomatic tension notes ("both perspectives have merit") are a failure.
- **Each reviewer stays in their lane.** PM doesn't critique hierarchy. Design doesn't rewrite copy. Content doesn't estimate effort.
- **Severity stays honest.** If everything is blocking, nothing is.
- **Review the right stage.** No pixel notes on a whiteboard sketch. No structural notes on something shipping Friday.
- **Don't manufacture conflict.** A lone dissent against three aligned disciplines is a finding.

## Use it for

- Pressure-testing a flow, screen, spec, prototype, or copy before a design review
- Prepping for a spec handoff or stakeholder presentation
- A gut check on "what am I missing" or "what would eng say"
