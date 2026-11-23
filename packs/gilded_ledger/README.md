# Demo: The Gilded Ledger

An `extension` pack for [DDDnD](https://github.com/mooeypoo/DDDnD). It retells the monolith story for **Gilded Ledger Co.**, a fictional payments company whose single payments monolith handles every charge, refund, and chargeback, with the regulator's audit approaching.

It is a demo of the most common reason to write a pack: a facilitator wants the game to speak their organization's language. It does that with very little new content:

| | From the base pack (by reference) | New in this pack |
|---|---|---|
| Scores | all six (clarity, craft, delivery, morale, trust, purse) | none |
| Stakeholders | CTO, Security Officer | Head of Payments, Customer Support Lead (with their own reaction rules) |
| Cards | 16, including Define Bounded Context and Introduce Anti-Corruption Layer | Split Out the Refunds Context, Add a Transactional Outbox, Freeze Changes to the Payment Path, Automate Nightly Reconciliation |
| Events | 6, including Critical Bug Discovered | Chargeback Storm, A Letter from the Regulator, Double-Charge Incident, The Audit Dry Run Goes Well |
| Aftershocks | the ones base cards schedule | Payment Events Become Trustworthy |
| Endings | all base outcome tiers and endings | none |
| Coupling | the base pack's three collapses (delivery, morale, trust) | none |

Because it builds on the base pack, its manifest declares `"depends_on": [{ "pack_id": "base", "version": "1.0.0" }]` and uses the GPL-3.0-only license (the base pack's license).

## Scenario

**The Gilded Ledger** (`ledger_payments_monolith`, 10 turns). Untangle a payments monolith before the regulator's audit. The Head of Payments wants nothing to break, Support hears about every problem first, and the CTO wants clear boundaries. Every refund is a negative payment, and every payment is a special case.

## Balance

The scenario passes DDDnD's content audit with no critical findings and no warnings. In 200 simulated runs, a bot that plays like a person (legal hand only) reaches the success tier about half the time and fails about one time in seven. That's a little harder than the base scenarios, on purpose: an audit deadline should feel tight.

## Loading it

```text
https://raw.githubusercontent.com/mooeypoo/DDDnD-packs/<tag>/packs/gilded_ledger/manifest.json
```

## Versions

- **1.1.0**: the scenario names the base pack's coupling rules (`coupling_rule_refs`). Until DDDnD made coupling part of content, the engine applied these three collapses to every scenario; now a scenario lists the ones it uses. 1.1.0 plays exactly like 1.0.0 did. Loaded in a DDDnD build with content coupling, 1.0.0 plays with no coupling at all. Needs a DDDnD build with coupling rules (M3).
- **1.0.0**: first release.

## Credits and license

Written by [Moriel Schottlender](https://moriel.tech). Licensed under GPL-3.0-only, like the DDDnD base pack it builds on.
