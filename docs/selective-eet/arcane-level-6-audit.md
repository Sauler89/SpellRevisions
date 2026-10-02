# Arcane Level 6 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks changes > IWDification > selected Spell Revisions v4.21 changes.

Spell Revisions v4.21 source is authoritative for SR behavior. Tactics Remix 8.2's documented spell-system changes are treated as higher-priority semantics, especially for mage chess and physical defenses.

| Spell | Decision | Reason |
|---|---|---|
| Invisible Stalker | SKIP / MIXED + SUMMON-ASSET RISK | SR replaces the summoned creature with a substantially stronger custom stalker but shortens duration from vanilla 9 hours to 8 hours. Importing SR summon assets can also bypass creature-side changes from the installed difficulty stack. Not a clean in-place buff. |
| Globe of Invulnerability | INCLUDE — ADAPTED | SR fixes duration at 2 turns, which is stronger than vanilla 1 round/level through caster level 19 but weaker above level 20. Use the better-of-both progression: 2 turns minimum through level 20, then vanilla 1 round/level scaling beyond 20. Core protection semantics remain untouched. |
| Tenser's Transformation | SKIP / ZSTWEAKS | ZSTweaks component 441 directly modifies Tenser's THAC0/APR behavior. Preserve ZS. SR is also a broad combat redesign. |
| Flesh to Stone | SKIP / MIXED SR REWORK | User does not use the ZSTweaks #444 Flesh to Stone tweak. Vanilla petrifies immediately on a failed Save vs. Spell. SR first slows the target for 3 rounds, then on the following round requires a Save vs. Petrification at -4 or petrifies it; it also explicitly excludes undead, constructs and incorporeal creatures and depends on SR's broader global petrification framework. The -4 save and Slow are buffs, but the one-round delay, changed save category, extra exclusions and infrastructure dependency make it a mixed redesign rather than a clean buff. Keep the installed/vanilla spell. |
| Death Spell | KEEP TACTICS / VANILLA | Preserve Death Spell completely because Tactics Remix relies on its existing semantics and additional interactions such as killing insect swarms. It is no longer consumed by the SR replacement. |
| Banishment | ADD AS NEW SPELL | Import SR Banishment as a separate dynamically allocated Level-6 Abjuration. It banishes hostile summoned creatures in a 30-ft. radius, allows no save, and ignores Magic Resistance. Death Spell remains fully intact. No WIZARD_BANISHMENT conflict was found in IWDification or ZSTweaks. |
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
| Stone to Flesh | KEEP VANILLA / SR DISABLES IT | User does not use the ZSTweaks #444 Stone to Flesh tweak. Vanilla is a normal Level-6 reversal of petrification. Full SR hides/disables WIZARD_STONE_TO_FLESH from spell selection and later reuses its scroll resource for another spell; the copied SR resource is therefore not an intended buffed player spell. Keep vanilla Stone to Flesh unchanged. |
| SR Monster Summoning VI / WIZARD_MONSTER_SUMMONING_4 | SKIP / DUPLICATE IWDIFICATION | IWDification already adds WIZARD_MONSTER_SUMMONING_4 as its coherent Level-6 Monster Summoning IV and distributes its scroll. SR uses the same semantic identifier for a differently named Monster Summoning VI. Retain IWDification. |
| Khelben's Warding Whip (Tactics-added Level 6) | KEEP TACTICS | Tactics Remix moves Khelben's Warding Whip from Level 7 to Level 6 as part of its mage-chess redesign. This is not an SR Level-6 change and must remain untouched. |

## Final selected set

### INCLUDE — ADAPTED
- Globe of Invulnerability — 2 turns minimum; from caster level 21 onward retain vanilla 1 round/level scaling
- Power Word Silence — SR 1-turn duration, vanilla Conjuration/Summoning school retained
- Contingency — Universal school only; installed mechanics/casting behavior retained

### ADD AS NEW SPELL
- Banishment — SR Banishment added as a separate dynamically allocated Level-6 Abjuration; Death Spell remains untouched

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
The user explicitly does not use ZSTweaks component 444 for Flesh to Stone / Stone to Flesh; those two spells are therefore compared directly against vanilla/SR instead.

Relevant enabled/group Level-6 overlaps:
- 390 — Acid Fog
- 441 — Tenser's Transformation
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

The three adapted changes are in-place revisions of existing spells:
- Globe of Invulnerability
- Power Word Silence
- Contingency

Banishment is genuinely new. Because SR normally replaces Death Spell and therefore reuses the Death Spell scroll, this project instead uses the dedicated learnable scroll resource `DVBANSCR.ITM`. Death Spell and its scroll remain untouched; `DVBANSCR.ITM` must be distributed dynamically during the unified EET arcane-scroll pass.

The deferred new-scroll list becomes:
- Obscuring Mist
- Dimension Jump
- Resist Elements
- Protection from Elemental Energy
- Mestil's Acid Sheath
- Banishment

## Status

**CLOSED for spell selection and implemented in component #0.**

Further Level-6 changes should be limited to technical fixes found during install/in-game testing or the deferred scroll-distribution pass.
