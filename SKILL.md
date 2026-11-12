---
name: kenshi-modding
description: Use when installing, creating, editing, translating, troubleshooting, or packaging Kenshi 1 mods, including Forgotten Construction Set (FCS), .mod files, Steam Workshop, mods.cfg, custom starts, dialogue, factions, towns, assets, or RE_Kenshi/KenshiLib plugins. Not for Kenshi 2 or unrelated games.
---

# Kenshi Modding

Use the installed editor and actual records as the source of truth. Distinguish a file installed successfully from a mod verified in game.

## Discover the current environment

Read [references/environment.md](references/environment.md) for this user's known installation and discovery procedure. Recheck paths on each machine; a known path is a hint, not authorization to modify everything below it. Record the game/FCS version, mod sources, dependencies, active order, and any RE_Kenshi installation relevant to the request. Preserve the user's manual workflow unless they request a different manager.

## Route by task

| Request | Read |
|---|---|
| Install/update/remove, Workshop, load order, backup/rollback | [installation.md](references/installation.md) |
| New mods, patches, balancing, dialogue, recruitment, factions, towns, research, translation, assets, native plugins | [authoring.md](references/authoring.md) |
| Crash, missing content, compatibility, saved-world state, release testing | [verification.md](references/verification.md) |

For exact fields or editor operations, consult the shipped `Using the FCS.pdf`, FCS property help, `fcs.def`, and `fcs_enums.def`. The manual documents the active output mod, errors, reference search, and bulk **Set Field** arithmetic. Read relevant sections; do not load the entire manual for every task. See [sources.md](references/sources.md) for maintained external references.

## Editing boundaries

- Ordinary content changes belong in a separate local mod or compatibility patch. Keep core `.base` files and subscribed Workshop sources intact. Do not merge overhauls merely to suppress conflicts.
- `.mod` and save files are structured binary data. Use FCS or a documented SDK tested on copies. Do not replace arbitrary bytes, invent a binary schema, or present renamed JSON as a functioning mod.
- Observe the FCS `*ACTIVE*` destination before saving. Keep dependencies loaded and preserve original StringIDs when overriding records; create distinct IDs for genuinely new records. Do not fabricate field names, conditions, or references.
- Make recoverable backups of affected existing files and activation configuration before mutation. Protect original saves; test imports on copies. Installing this skill grants no authority to modify saves or publish content.
- File presence alone does not prove a hook is loaded or a mod works. Report separately: prepared, installed, reopened in FCS, and tested in game. State any unavailable tools or unperformed checks.

## Example: reduce weapon base prices by 20%

In a new patch, load the source mod and dependencies. Find the actual price-driving records and property help rather than assuming a field called `price`. Select only intended records, use **Set Field** multiplication by `0.8` if applicable, inspect rounding and shared references, then review the change list. Reopen the patch, rescan errors, and compare representative shop transactions in a disposable test save; vendor modifiers may affect observed prices.

## Common mistakes

Numeric Workshop folders are not automatically valid local FCS mod folders. Activation order is not evidence that two mods are compatible. Missing dependency records should be investigated before cleanup deletes references. Importing a save is not a universal repair for faulty records.
