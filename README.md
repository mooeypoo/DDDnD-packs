# DDDnD Packs

Content packs for [DDDnD — Domain-Driven Design n' Dragons](https://github.com/mooeypoo/DDDnD), the game where you sit at a war table, play architecture cards, and shape a living software system before the turns run out. Play it at [dddnd.app](https://dddnd.app).

A **content pack** is a folder of JSON files (scenarios, cards, stakeholders, events, and more) plus a `manifest.json` that describes it. DDDnD's engine reads packs as data. Packs never contain code, so a pack can change the story and the numbers, but it can't make the game do anything else.

This repository holds packs published outside the game itself: demos that show what a pack can do, and, over time, other examples and working packs that facilitators can use in their own workshops.

> **Status:** loading packs into the game is still in development. It is switched off on dddnd.app until it is ready. The packs here are built and checked against the same rules the game will use.

## Packs in this repository

| Pack | Folder | Kind | What it is |
|---|---|---|---|
| Demo: The Gilded Ledger | [`packs/gilded_ledger`](packs/gilded_ledger) | `extension` of the base pack | The monolith story retold for a fictional payments company, built on the base pack's scores, cards, and endings. A model for the most common workshop use: "our system, our stakeholders, our politics". |

Being in this repository does not mean a pack is endorsed by DDDnD. If DDDnD ever endorses packs, that list will live in the [official DDDnD repository](https://github.com/mooeypoo/DDDnD), where nobody outside the project can edit it.

## Loading a pack

Each pack is loaded by the URL of its `manifest.json`, pinned to a release tag so the content can't change under a saved game:

```text
https://raw.githubusercontent.com/mooeypoo/DDDnD-packs/<tag>/packs/<pack_id>/manifest.json
```

The game shows who made the pack, its license, and where it comes from before anything is loaded. Packs are only loaded from GitHub (raw files or GitHub Pages) or from a file on your own computer.

## Repository layout

```text
DDDnD-packs/
  README.md
  LICENSE
  packs/
    <pack_id>/              one folder per pack; the folder name is the pack id
      README.md             what the pack is for and how to use it
      manifest.json         pack metadata, entry points, and file inventory
      scenarios/
      cards/
      stakeholders/
      stakeholder-reaction-rules/
      events/
      delayed-effects/
      ...                   only the folders the pack needs
```

Every pack is self-contained. Packs in this repository never share files, and if one pack builds on another, it says so in its `depends_on`, the same as any other pack.

## Adding a pack

1. **Create `packs/<pack_id>/`** with a `manifest.json` and a `README.md`. The [DDDnD content pack authoring guide](https://github.com/mooeypoo/DDDnD/blob/main/docs/CONTENT_PACK_AUTHORING_GUIDE.md) explains every file and field.
2. **Use `"base_url": "."`** in the manifest, so the pack works from any tag without edits.
3. **Prefix your content ids** with a short, pack-specific word (the Gilded Ledger uses `ledger_`). Content ids are shared across all loaded packs, and the game refuses a pack whose files collide with another pack's.
4. **Pick a license.** A pack that depends on the base pack must use `GPL-3.0-only` or `GPL-3.0-or-later`, because the base pack is GPL-3.0. A standalone pack may use any valid SPDX license.
5. **Validate and balance-check it** with DDDnD's own validator. From a DDDnD checkout next to this repository:

   ```bash
   npx tsx scripts/validate-content-pack.ts \
     --content-root ../DDDnD-packs/packs/<pack_id> \
     --audit --runs 50 --fail-on-audit-critical
   ```

   The validator checks every file against the game's schema and builds each scenario with the packs it depends on. With `--audit`, it also plays the scenario hundreds of times with a bot and reports balance problems (stakeholders who only ever decline, unfair event pools, dominant strategies). This repository runs the same check on every push.

### Editor support

Every content file can point to its JSON Schema for autocomplete and inline errors:

```json
{
  "$schema": "https://dddnd.app/schema/v1/card.schema.json",
  "id": "ledger_split_refunds_context"
}
```

This repository's `.vscode/settings.json` maps the schemas to the pack folders automatically.

## License

This repository is licensed under the [GNU General Public License v3.0](LICENSE). Each pack also declares its license in its `manifest.json`.

## Credits

Created by [Moriel Schottlender](https://moriel.tech), as part of [DDDnD](https://github.com/mooeypoo/DDDnD).
