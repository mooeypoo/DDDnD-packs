# SRE: The Pager Storm

An `extension` pack for [DDDnD](https://github.com/mooeypoo/DDDnD) that takes the game to a second domain: **site reliability engineering and incident response**. Where the base game is about domain boundaries and a tangled monolith, this pack is about keeping a service up without burning out the people who keep it up.

It is also the test that DDDnD's engine is truly content-driven: nothing in this pack exists in DDDnD's code. Its scores, endings, classes and coupling are all plain JSON, and the game picks them up as it does the base game's.

## What it teaches

- Reliability is a budget you spend, not a virtue.
- Heroics feel good, and burn people out.
- Blameless learning beats blame.
- Toil compounds.

## Scenario

**The Pager Storm** (`sre_pager_storm`, 10 turns). A growing service pages its on-call team every night. The SLOs are vague, the error budget is nearly spent, and the people holding the pager are running out of sleep. Make the service reliable without burning out the team, or stopping the company from shipping.

## What's in it

| | New in this pack | From the base pack |
|---|---|---|
| Scores | Availability (Uptime), Error Budget, Rested On-Call (Rest), Customer Trust, Change Velocity, Observability (Sight) | none |
| Council | VP of Engineering, Product Lead, Customer Support Lead, Finance Director, On-Call Engineer, each with two reaction rules | none |
| Cards | 22: define SLOs, an error-budget policy, runbooks, blameless postmortems, alert tuning, a feature freeze, automated rollbacks, chaos drills, paying down toil, a heroic 3 a.m. fix, shipping anyway, and more | none |
| Events | 14: the 3 a.m. outage, a cascading failure, a cloud region down, an alert storm, "root cause by noon", an expired certificate, and some good news | none |
| Aftershocks | 7, from cards whose payoff comes later (runbooks, rollbacks, chaos drills, canaries…) | none |
| Coupling | Burnout Spiral (an exhausted on-call weakens availability and observability gains), Error Budget Exhausted, Flying Blind | none |
| Endings | The Hero Firefighter, Pager-Haunted, The Reliability Architect, The Error-Budget Accountant, The Toil Slayer, The Steady Operator | none |
| Outcome tiers | none | Triumph, Success, Survival, Struggle, Collapse |
| Classes | Pager Paladin (+1 Uptime), Signal Seer (+1 Sight), Toil Druid (+1 Rest), Budget Keeper (+1 Error Budget) | none fit: the base classes favor scores this pack doesn't have, so its table doesn't offer them |
| Challenge modifiers | Launch Week, Skeleton Crew | Speed Run (it changes only the number of turns, so it fits) |

All content ids start with `sre_`.

### The endings

Endings are checked from the top down; the first one whose conditions all hold is yours.

| Ending | When |
|---|---|
| The Hero Firefighter | Availability went up by 5 or more while Rest fell by 8 or more |
| Pager-Haunted | Rest ended below 25 |
| The Reliability Architect | Availability and Observability together rose by 32 or more, and Rest ended at 50 or above |
| The Error-Budget Accountant | Error Budget ended at 52 or above, and Change Velocity at 45 or above |
| The Toil Slayer | Rest rose by 15 or more |
| The Steady Operator | Otherwise |

## Balance

The scenario passes DDDnD's content audit with no critical findings and no warnings. In 500 simulated runs, a bot that plays like a person (legal hand only) reaches the success tier about 40% of the time, across several seeds. The lobby marks it **Normal**. Every ending is reached. The Hero Firefighter and Pager-Haunted are rare for the bot, which plays a balanced hand; repeated heroic fixes (each costs 6 Rest) lead there.

## Loading it

```text
https://raw.githubusercontent.com/mooeypoo/DDDnD-packs/<tag>/packs/sre_on_call/manifest.json
```

Needs a DDDnD build with content-driven endings, coupling and tiers, and pack-owned classes (M3).

## Versions

- **1.0.0**: first release.

## Credits and license

Written by [Moriel Schottlender](https://moriel.tech). Licensed under GPL-3.0-only, like the DDDnD base pack it builds on.
