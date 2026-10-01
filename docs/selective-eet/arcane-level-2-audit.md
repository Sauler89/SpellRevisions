# Arcane Level 2 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks spell tweaks > IWDification > selected Spell Revisions v4.21 changes.

The public Spell Revisions documentation is useful as a comparison reference, but it is still labelled as last updated for SR v4b18. When the documentation and the supplied v4.21 source differ, this audit follows the actual v4.21 source that will be installed.

| Spell | Decision | Reason |
|---|---|---|
| Blur | SKIP / MIXED | SR greatly extends duration and improves saves vs. spell from +1 to +3, but vanilla grants +1 to all saves while SR drops the non-spell save bonuses. Not a pure buff. |
| Detect Evil | KEEP VANILLA | SR deprecates the level-2 Detect Evil slot as part of its Detect Alignment/Know Opponent restructuring. This project will not remove Detect Evil. |
| Detect Alignment | ACCEPT REPLACEMENT — replaces Know Alignment | Use SR's Detect Alignment in place of Know Alignment. Keep it as the SR Level-1 arcane replacement, and remove/disable the old Know Alignment availability rather than keeping both spells. Detect Evil remains untouched. |
| Detect Invisibility | SKIP / MIXED | SR repeats detection every round for 5 rounds, but reduces the detection radius substantially and changes what the spell reveals. Useful redesign, not a pure buff. |
| Horror | SKIP / ZSTWEAKS + MIXED | ZSTweaks component 210 owns Horror's school/projectile presentation. Independently, SR doubles the AoE/range but cuts duration from 1 turn to 5 rounds. Not a pure buff. |
| Invisibility | SKIP / MIXED | SR reduces maximum duration from 24 hours to 8 hours and changes permitted actions while invisible. This is a behavioral rebalance, not a clean buff. ZSTweaks True Sight compatibility may also patch this resource. |
| Battering Ram | ACCEPT REPLACEMENT — replaces Knock | Use SR's intended replacement directly: SPWI207 / SCRL91 become Battering Ram. Knock is not retained as a separate arcane spell. |
| Know Alignment | REPLACED BY DETECT ALIGNMENT | Do not keep Know Alignment as a separate arcane spell. Its role is replaced by SR's Detect Alignment. |
| Know Opponent | SKIP | Upstream SR v4.21 does contain an arcane Know Opponent at SPWI208, but it is not part of the desired spell list for this project. Do not import it. |
| Luck | SKIP / TACTICS REMIX + ZSTWEAKS | Tactics Remix directly extends Luck, and ZSTweaks component 145 can further boost both duration and effect. Preserve the higher-priority result. |
| Resist Fear | SKIP / MIXED | SR gives explicit fear immunity but cuts the duration from vanilla's 1 hour to 5 turns. Not a pure buff. |
| Melf's Acid Arrow | SKIP / ZSTWEAKS | SR adds 1d6 missile damage on impact and is otherwise a clear offensive improvement, but ZSTweaks component 447 substantially patches the spell and can make the conjured acid bypass MR. Preserve ZSTweaks. If component 447 is ever disabled, SR's version becomes a valid INCLUDE candidate. |
| Mirror Image | SKIP / MIXED | SR gives a long fixed 5-turn duration and deterministic image scaling, but casting time worsens from 1 to 2 and low-level image count can be less favorable than vanilla. Not a pure buff. |
| Stinking Cloud | SKIP / MIXED | SR doubles the radius and removes vanilla's +2 save bonus, but replaces the stronger knockdown/unconscious-style disable with a 1-round nausea that still allows movement. Rebalance, not pure buff. |
| Strength | INCLUDE | Same core Strength-setting behavior as vanilla, but casting time improves dramatically from 9 to 2. Clean buff. |
| Web | SKIP / TACTICS REMIX + ZSTWEAKS | Tactics Remix and ZSTweaks both deliberately modify Web. Preserve the priority stack. |
| Agannazar's Scorcher | SKIP / MIXED | SR greatly extends range and makes the persistent flame line more useful, but spreads the second 3d6 pulse into a later round instead of vanilla's faster burst. ZSTweaks also removes the caster-pause behavior. Not a pure SR buff. |
| Ghoul Touch | INCLUDE — ADAPTED | SR is a major buff: +4 to hit, +1 effective enchantment, 1d8 magic damage, longer charge duration, and a -1 save vs. Death for paralysis. Preserve vanilla casting time 1 instead of importing SR's slower casting time 2. |
| Vocalize | SKIP / NO MATERIAL BUFF | SR is effectively the vanilla spell mechanically. No reason to overwrite it. |
| Power Word Sleep | INCLUDE — ADAPTED | Vanilla simply fails against targets at 20+ HP. SR retains the irresistible sleep against 1–19 HP but allows targets at 20+ HP to be affected if they fail a save. Clear buff. Preserve the vanilla Conjuration school rather than importing SR's unrelated school change. |
| Ray of Enfeeblement | SKIP / MIXED | SR adds a -2 save penalty, -3 attack/damage and 50% movement reduction, but replaces vanilla's potentially much stronger Strength=5 effect and changes duration scaling. ZSTweaks component 370 also changes its school/presentation. |
| Chaos Shield | SKIP / NERF | Wild-surge bonus remains +15, while SR's 2 rounds/level duration is generally shorter than vanilla from mid levels onward. |
| Sound Burst | ACCEPT REPLACEMENT — replaces Deafness | Use SR's intended replacement directly. Deafness is not retained as a separate arcane spell. |
| Glitterdust | SKIP / MIXED | SR guarantees a smaller -2 attack penalty and improved anti-invisibility behavior, but removes vanilla's stronger save-or-blind (-4 attack and AC) effect. Not a pure buff. |
| Resist Elements | ADD AS NEW SPELL | Useful new Level-2 Abjuration: +25% resistance to all elemental damage for 1 turn + 1 round/level. No IWDification duplicate was found. |
| Monster Summoning II | SKIP / DUPLICATE IWDIFICATION | IWDification already adds a spell named Monster Summoning II (its IWD Level-4 version). Avoid a second same-name spell at a different level and retain IWDification. |

## Proposed selected set

Existing spells to buff:
- Strength
- Ghoul Touch (SR mechanics, vanilla casting time retained)
- Power Word Sleep (SR mechanics, vanilla school retained)

Accepted replacements:
- Battering Ram replaces Knock
- Sound Burst replaces Deafness
- Detect Alignment replaces Know Alignment and remains the SR Level-1 arcane replacement

New Level-2 spell:
- Resist Elements

Explicitly excluded:
- Know Opponent

## Priority-mod overlaps

### Tactics Remix 8.2
At Arcane Level 2, the supplied Spell Tweaks component actively changes:
- Luck
- Web

Its Detect Invisibility block is IWDEE-only and is therefore not an EET conflict.

### ZSTweaks
Relevant enabled/user-defined Arcane Spell Tweaks include:
- Luck (145)
- Horror (210)
- Ray of Enfeeblement (370)
- Melf's Acid Arrow (447)
- Agannazar's Scorcher (558)
- Web (561)

Additional ZSTweaks components can also touch Invisibility and selected divinations / Glitterdust / Stinking Cloud for True Sight or MR-bypass behavior. The selected set above avoids overwriting those resources.

## Scroll roadmap

Scroll handling for replacements should follow the replaced vanilla resources where appropriate:

- Battering Ram reuses Knock's spell/scroll slot (SPWI207 / SCRL91).
- Sound Burst reuses Deafness's spell/scroll slot.
- Detect Alignment replaces Know Alignment; its final Level-1 scroll handling must preserve the intended SR move while removing the old Know Alignment availability.
- Resist Elements is a genuinely new spell and therefore needs its own learnable scroll plus later EET distribution.

The genuinely new-scroll distribution pass will still be handled together with Obscuring Mist and Dimension Jump after the arcane spell selection is complete.
