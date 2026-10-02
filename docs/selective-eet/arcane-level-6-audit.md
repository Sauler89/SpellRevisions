# Arcane Level 6 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks changes > IWDification > selected Spell Revisions v4.21 changes.

Spell Revisions v4.21 source is authoritative for SR behavior. Tactics Remix 8.2's documented spell-system changes are treated as higher-priority semantics, especially for mage chess and physical defenses.

| Spell | Decision | Reason |
|---|---|---|
| Invisible Stalker | SKIP / MIXED + SUMMON-ASSET RISK | SR replaces the summoned creature with a substantially stronger custom stalker but shortens duration from vanilla 9 hours to 8 hours. Importing SR summon assets can also bypass creature-side changes from the installed difficulty stack. Not a clean in-place buff. |
| Globe of Invulnerability | INCLUDE — ADAPTED | SR fixes duration at 2 turns, which is stronger than vanilla 1 round/level through caster level 19 but weaker above level 20. Use the better-of-both progression: 2 turns minimum through level 20, then vanilla 1 round/level scaling beyond 20. Core protection semantics remain untouched. |
| Tenser's Transformation | SKIP / ZSTWEAKS | ZSTweaks component 441 directly modifies Tenser's THAC0/APR behavior. Preserve ZS. SR is also a broad combat redesign. |
| Flesh to Stone | SKIP / ZSTWEAKS | ZSTweaks component 444 directly modifies Flesh to Stone's saving throw/immunity behavior. Preserve ZS. |
| Death Spell / SR Banishment | SKIP / TACTICS SEMANTICS + REPLACEMENT | SR completely replaces Death Spell with Banishment, which only removes hostile summons. Tactics Remix explicitly relies on Death Spell for additional interactions such as killing insect swarms. Preserve Death Spell. |
| Protection from Magic Energy | SKIP / NO MATERIAL BUFF | SR retains the same essential 100% magic-damage protection, duration, range and casting time. No meaningful reason to overwrite the installed spell. |
| Mislead | SKIP / ZSTWEAKS + MIXED | ZSTweaks component 582 patches Mislead as part of its True Sight/invisibility system. SR also fixes the decoy to 6 rounds instead of letting it naturally match the caster's scaling spell duration. Preserve ZS. |
| Pierce Magic | SKIP / TACTICS MAGE CHESS | Tactics Remix moves Pierce Magic to Level 8 and makes it function as vanilla Pierce Shield. The Level-6 SR/vanilla resource semantics must not be restored over Tactics. |
| True Sight / True Seeing | SKIP / ZSTWEAKS | ZSTweaks component 582 directly rewrites True Sight/True Seeing behavior and invisibility interactions. Preserve ZS. |
| Protection from Magical Weapons | SKIP / TACTICS REMIX | Tactics Remix's physical-defense overhaul transforms Protection from Magical Weapons into Lesser Mantle. Preserve Tactics' resource semantics. |
| Power Word Silence | INCLUDE — ADAPTED | SR extends duration from vanilla 7 rounds to 1 turn. Preserve vanilla Conjuration/Summoning school and all installed mechanics; patch duration only. Strict buff. |
| Improved Haste | SKIP / ZSTWEAKS | ZSTweaks component 577 directly rebuilds Improved Haste duration scaling. Preserve ZS. |
| Death Fog / SR Acid Fog | SKIP / ZSTWEAKS | ZSTweaks component 390 directly rebuilds Acid/Death Fog damage and immunity handling. Preserve ZS rather than applying SR's replacement. |
| Chain Lightning | SKIP / ZSTWEAKS | ZSTweaks component 451 directly improves Chain Lightning damage/projectile behavior. Preserve ZS. |
| Disintegrate | SKIP / ZSTWEAKS | ZSTweaks component 522 directly patches Disintegrate and its target-specific handling. Preserve ZS. |
| Contingency | INCLUDE — ADAPTED | SR makes Contingency Universal, removing specialist-school exclusion, but otherwise does not provide a clean mechanical improvement worth importing wholesale. Change only the school to Universal; retain the installed Contingency mechanics and casting behavior. |
| Spell Deflection | SKIP / TACTICS MAGE CHESS | SR disables the Level-6 Spell Deflection because its spell-deflection ladder is reorganized. Tactics mage chess explicitly uses Spell Deflection/Turning as protection types, including for Breach interaction. Preserve the installed Level-6 spell. |
| Conjure Fire Elemental | SKIP / IWDIFICATION + TACTICS | IWDification owns/normalizes the elemental summoning family, while Tactics Remix has its own Tougher Elementals creature hierarchy. Do not replace summon assets with SR versions. |
| Conjure Air Elemental | SKIP / IWDIFICATION + TACTICS | Same reasoning as Fire Elemental. Preserve the installed elemental family and creature hierarchy. |
| Conjure Earth Elemental | SKIP / IWDIFICATION + TACTICS | Same reasoning as Fire/Air Elemental. |
| Carrion Summons / SR Animate Skeleton Warrior | SKIP / REPLACEMENT + SUMMON SEMANTICS | SR completely replaces Carrion Summons with a Skeleton Warrior summon. This removes an existing spell rather than strictly improving it and injects custom undead summon assets into an installation where Tactics already modifies undead behavior. Preserve Carrion Summons. |
| Summon Nishruu | SKIP / LEVEL-SHIFT NERF | SR moves Summon Nishruu from Level 6 to Level 7 while replacing the summon implementation. This project does not accept the spell-level nerf; retain the installed Level-6 spell. |
| Stone to Flesh | SKIP / ZSTWEAKS | ZSTweaks component 444 also patches Stone to Flesh and adds special interaction with stone golems. Preserve ZS. |
| SR Monster Summoning VI / WIZARD_MONSTER_SUMMONING_4 | SKIP / DUPLICATE IWDIFICATION | IWDification already adds WIZARD_MONSTER_SUMMONING_4 as its coherent Level-6 Monster Summoning IV and distributes its scroll. SR uses the same semantic identifier for a differently named Monster Summoning VI. Retain IWDification. |
| Khelben's Warding Whip (Tactics-added Level 6) | KEEP TACTICS | Tactics Remix moves Khelben's Warding Whip from Level 7 to Level 6 as part of its mage-chess redesign. This is not an SR Level-6 change and must remain untouched. |

## Proposed selected set

### INCLUDE — ADAPTED
- Globe of Invulnerability — 2 turns minimum; from caster level 21 onward retain vanilla 1 round/level scaling
- Power Word Silence — SR 1-turn duration, vanilla Conjuration/Summoning school retained
- Contingency — change school to Universal only; retain installed mechanics/casting behavior

Everything else remains with vanilla, Tactics Remix, ZSTweaks or IWDification.

## Priority-mod notes

### Tactics Remix 8.2
Relevant Level-6 semantics:
- Pierce Magic is moved to Level 8 and acts as vanilla Pierce Shield.
- Khelben's Warding Whip is moved to Level 6.
- Breach is blocked by Spell Deflection, Spell Turning and Spell Trap; therefore the protection ladder must retain Tactics semantics.
- Protection from Magical Weapons becomes Lesser Mantle in the full physical-defense overhaul.
- Death Spell retains additional Tactics interactions, including killing insect swarms.
- Tactics' mage scripts are explicitly written around vanilla/Tactics spell semantics rather than full Spell Revisions replacements.

### ZSTweaks
Relevant enabled/group Level-6 overlaps:
- 390 — Acid Fog
- 441 — Tenser's Transformation
- 444 — Flesh to Stone / Stone to Flesh
- 451 — Chain Lightning
- 522 — Disintegrate
- 577 — Haste / Improved Haste duration scaling
- 582 — True Sight/True Seeing and player invisibility sources including Mislead

These resources are therefore not overwritten by this Level-6 module.

### IWDification
Relevant ownership:
- WIZARD_MONSTER_SUMMONING_4 is already added as the IWD Level-6 Monster Summoning IV and has its own distribution.
- The elemental summoning family is normalized by IWDification, including Water Elemental additions.
- Several additional IWD Level-6 spells occupy their own dynamically assigned/resources and are not affected by the proposed selection.

## Scroll implications

All three proposed changes are in-place revisions of existing spells:
- Globe of Invulnerability
- Power Word Silence
- Contingency

No new Level-6 scroll resource or distribution work is required.

The deferred new-scroll list remains:
- Obscuring Mist
- Dimension Jump
- Resist Elements
- Protection from Elemental Energy
- Mestil's Acid Sheath

## Status

**OPEN — awaiting user approval of the proposed Level-6 selection before implementation in component #0.**
