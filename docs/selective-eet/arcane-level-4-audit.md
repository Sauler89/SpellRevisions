# Arcane Level 4 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks changes > IWDification > selected Spell Revisions v4.21 changes.

Primary sources for this audit are the supplied Spell Revisions v4.21, Tactics Remix 8.2, IWDification and ZSTweaks source packages.

| Spell | Decision | Reason |
|---|---|---|
| Confusion | INCLUDE — ADAPTED | SR doubles the area (15 ft. -> 30 ft.) while retaining the same effective range and -2 Spell save. SR shortens vanilla's scaling duration to a fixed 5 rounds. Import the SR AoE improvement but retain vanilla's 5 rounds + 1 round/6 levels duration, making this a strict buff. |
| Dimension Door | KEEP VANILLA | SR disables Dimension Door because it introduces Dimension Jump. This project already added Dimension Jump separately at Level 1, so Dimension Door remains available as its own spell. |
| Fire Shield (Blue) | SKIP / TACTICS REMIX | Tactics Remix Spell Tweaks directly patches both Fire Shields and their interaction/repeating-damage behavior. SR also repurposes the blue slot around Mestil's Acid Sheath. Preserve Tactics and the existing spell. |
| Ice Storm | SKIP / TACTICS REMIX + ZSTWEAKS | Tactics Remix adds its area/damage-type handling to Ice Storm and ZSTweaks component 220 further modifies its damage. Do not overwrite either. |
| Improved Invisibility | SKIP / ZSTWEAKS | ZSTweaks component 582 directly patches player invisibility sources, including SPWI405, for its True Sight behavior. SR also drops the vanilla +4 Saving Throw bonus from the description/implementation path. Preserve ZS. |
| Minor Globe of Invulnerability | SKIP / MIXED | SR changes duration from 1 round/level to a fixed 2 turns. This is a large buff at ordinary acquisition levels but becomes shorter than vanilla at sufficiently high caster levels. No other material SR benefit justifies replacing it. |
| Monster Summoning II / old SR summoning slot | SKIP / IWDIFICATION | IWDification owns WIZARD_MONSTER_SUMMONING_2 / SPWI407 as the Level-4 step of its coherent Monster Summoning progression. Do not deprecate or overwrite it. |
| Stoneskin | SKIP / NERF | SR reduces duration from vanilla 12 hours to 8 hours without a compensating mechanical buff relevant to this project. |
| Contagion | SKIP / ZSTWEAKS | ZSTweaks component 380 substantially changes Contagion's ability-score penalties. Preserve ZS. SR is also a redesign rather than a clean buff. |
| Break Enchantment / Remove Curse | ACCEPT REPLACEMENT — ADAPTED | SR greatly expands Remove Curse into Break Enchantment: it can also cure confusion, feeblemind, petrification, magical sleep and charm, and gains range. Preserve vanilla casting time 4 instead of SR's 5. If ZSTweaks component 1589 has added its Rashad's Talon interaction to SPWI410, preserve that effect when applying the replacement rather than overwriting it. |
| Emotion: Despair / Emotion: Hopelessness | SKIP / IWDIFICATION | IWDification directly owns SPWI411 as its Emotion: Hopelessness implementation and integrates it with the IWD Emotion spell family. SR's Emotion: Despair would overwrite that priority spell and is also a different, weaker control paradigm. |
| Greater Malison | SKIP / MIXED | Vanilla applies -4 to all saves. SR reduces this to -2, adds -1 Luck, doubles the radius and uses a fixed 2-turn duration. Useful redesign, but not a strict buff and weaker as a pure save debuff. |
| Otiluke's Resilient Sphere | SKIP / ZSTWEAKS | ZSTweaks component 487 substantially rebuilds targeting/innocent handling and casting behavior for SPWI413. Preserve ZS. |
| Spirit Armor | SKIP / NERF-MIXED | SR shortens duration (2 hours -> 10 turns), worsens casting time (3 -> 4), and changes the +3 save bonus from Spell to Death. Not a buff. |
| Polymorph Other | SKIP / MIXED | SR gives weak targets a -3 save penalty but high-level targets a +3 bonus. Stronger against weak enemies, weaker against the enemies where the spell most needs help. |
| Polymorph Self | SKIP / MIXED | SR substantially reworks forms and adds Winter Wolf, but changes form statistics and fixes duration at 5 turns instead of vanilla's scaling duration. Not a pure upgrade across levels/forms. |
| Enchanted Weapon | SKIP / NO RELEVANT EET SR MECHANIC | The current SR main component does not replace the EE/EET Enchanted Weapon mechanics; on Enhanced Editions it only supplies icon assets. Nothing meaningful to import. |
| Fire Shield (Red) | SKIP / TACTICS REMIX | Tactics Remix Spell Tweaks directly patches both Fire Shields, including mutual exclusion/resource handling and repeating backlash behavior. Preserve Tactics. |
| Secret Word | INCLUDE — ADAPTED | SR improves casting time from 4 to 1 and increases range, but lowers the stated maximum affected protection from 8th to 7th level and changes the school. Patch the existing spell instead: keep vanilla Abjuration and vanilla protection-removal coverage, while importing only SR's casting-time/range buffs. |
| Minor Sequencer / Simbul's Spell Matrix | SKIP / NO MATERIAL BUFF | SR mainly renames/reframes Minor Sequencer as Simbul's Spell Matrix and makes it Universal. Its 1-round casting time is not an improvement over vanilla casting time 9, and the core two-spell/Level-2-or-lower functionality remains the same. |
| Teleport Field | SKIP / MIXED | SR doubles the radius and increases range, but adds a Saving Throw vs. Spell at -4 to an effect that is unavoidable in vanilla. Not a pure buff. |
| Monster Summoning IV / Spider Spawn | SKIP / IWDIFICATION STRUCTURAL CONFLICT | SR replaces Spider Spawn with a Level-4 Monster Summoning IV. IWDification already provides Monster Summoning II at Level 4 and its own later Monster Summoning III/IV progression. Keep Spider Spawn and the IWD summoning progression. |
| Farsight | INCLUDE | Same utility as vanilla, but SR extends duration to 5 turns. Within normal EET wizard levels this is a straight duration buff. |
| Wizard Eye | SKIP / NO BUFF | SR retains the same basic function/duration but uses Short range and 1-round casting time; vanilla has visual-range targeting and casting time 9. No worthwhile upgrade. |
| Protection from Elemental Energy | ADD AS NEW SPELL | Useful new Level-4 Abjuration granting 100% protection from one selected element (acid, cold, fire or lightning) for 1 turn/level. No equivalent spell was found in Tactics Remix, IWDification or ZSTweaks. Must use ADD_SPELL dynamically because IWDification already occupies SPWI426 with Shadow Monsters. |
| Vitriolic Sphere | SKIP / DUPLICATE IWDIFICATION | IWDification already adds and distributes Vitriolic Sphere. SR is slightly stronger at the earliest acquisition level in a perfect failed-save case, but IWDification scales with caster level and overtakes it quickly while reaching much higher damage. SR is not clearly superior, so retain IWDification. |

## Proposed selected set

### INCLUDE — ADAPTED
- Confusion — SR 30-ft. AoE, vanilla range and scaling duration retained
- Break Enchantment — replaces Remove Curse; retain vanilla casting time 4 and preserve any existing ZSTweaks Rashad's Talon hook
- Secret Word — retain vanilla Abjuration/protection coverage, import SR casting time 1 and longer range

### INCLUDE
- Farsight — SR duration buff

### ADD AS NEW SPELL
- Protection from Elemental Energy — dynamically allocated Level-4 spell

Everything else remains vanilla or belongs to Tactics Remix, ZSTweaks or IWDification.

## Priority-mod notes

### Tactics Remix 8.2
Relevant Level-4 spell changes in the supplied source:
- Fire Shield (Blue) and Fire Shield (Red): directly modified by Spell Tweaks, including mutual resource protection and repeating backlash handling.
- Ice Storm: patched by Tactics' initialization logic for area/damage-state handling.

### ZSTweaks
Relevant enabled/group changes touching Level-4 resources:
- 220 — Ice Storm
- 380 — Contagion
- 487 — Otiluke's Resilient Sphere
- 582 — True Sight compatibility patches Improved Invisibility and other invisibility sources
- 1589 — Rashad's Talon adds a specific interaction to Remove Curse/SPWI410; if Break Enchantment is installed, this existing effect must be preserved
- 2231 reads/uses Fire Shield (Red) for Dragon Disciple spell access, while Tactics already owns the actual Fire Shield mechanics

### IWDification
Direct Level-4/resource conflicts:
- SPWI407 = WIZARD_MONSTER_SUMMONING_2
- SPWI411 = WIZARD_EMOTION_HOPELESSNESS
- SPWI426 = WIZARD_SHADOW_MONSTERS
- SPWI432 = WIZARD_VITRIOLIC_SPHERE

Therefore:
- never hardcode the new Protection from Elemental Energy to SPWI426;
- do not import SR's Emotion: Despair over SPWI411;
- do not import SR's summoning replacement over the IWD Monster Summoning progression;
- retain IWDification's Vitriolic Sphere.

## Scroll implications

In-place changes inherit existing scroll distribution:
- Confusion
- Break Enchantment (replaces Remove Curse)
- Secret Word
- Farsight

Protection from Elemental Energy is genuinely new. It is implemented with a dynamically allocated spell resource and four hidden SR-derived elemental-protection subspells, so it always grants the advertised 100% protection without overwriting the retained Tactics/vanilla protection spells. It uses the dedicated learnable scroll resource `DVPEESCR.ITM`, which still needs dynamic EET distribution during the unified arcane-scroll pass.

Deferred new-scroll list now includes:
- Obscuring Mist
- Dimension Jump
- Resist Elements
- Protection from Elemental Energy

## Status

**CLOSED for spell selection and implemented in component #0.**

Further Level-4 changes should be limited to technical fixes found during install/in-game testing or the deferred scroll-distribution pass.
