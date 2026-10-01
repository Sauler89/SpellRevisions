# Arcane Level 2 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks spell tweaks > IWDification > selected Spell Revisions v4.21 changes.

The public Spell Revisions documentation remains useful as a comparison reference, but where it differs from the supplied v4.21 source this project follows the actual v4.21 source.

| Spell | Decision | Reason |
|---|---|---|
| Blur | SKIP / MIXED | SR greatly extends duration and improves saves vs. spell, but vanilla grants a bonus to all saves while SR drops the non-spell save bonuses. |
| Detect Evil | KEEP | Detect Evil remains untouched. It is not consumed by the Detect Alignment replacement used in this project. |
| Detect Alignment | ACCEPT REPLACEMENT — replaces Know Alignment | Use SR's Detect Alignment as the full replacement for Know Alignment and move it to arcane Level 1, as intended by SR. The old Know Alignment resource remains only as a hidden compatibility alias so already-compiled scripts/CRE references still execute Detect Alignment. |
| Detect Invisibility | SKIP / MIXED | SR repeats detection but reduces the radius and changes reveal behavior. |
| Horror | SKIP / ZSTWEAKS + MIXED | ZSTweaks owns the selected Horror behavior; SR also trades duration for range/AoE. |
| Invisibility | SKIP / MIXED | SR shortens maximum duration and changes what actions preserve invisibility. |
| Battering Ram | ACCEPT REPLACEMENT — replaces Knock | Full SR replacement. SPWI207/SCRL91 become Battering Ram; Knock is not kept as a separate spell. |
| Know Alignment | REPLACED | Completely replaced by Detect Alignment. No separately learnable Know Alignment remains. |
| Know Opponent | SKIP | SR v4.21 contains an arcane SPWI208 Know Opponent, but it is intentionally excluded from this project. |
| Luck | SKIP / TACTICS REMIX + ZSTWEAKS | Preserve the higher-priority Luck result. |
| Resist Fear | SKIP / MIXED | Explicit fear immunity but substantially shorter duration. |
| Melf's Acid Arrow | SKIP / ZSTWEAKS | The selected ZSTweaks component owns this spell. |
| Mirror Image | SKIP / MIXED | Longer fixed duration but slower casting and potentially less favorable low-level image count. |
| Stinking Cloud | SKIP / MIXED | Better radius/save pressure but weaker disable behavior. |
| Strength | INCLUDE | Same core spell with casting time improved from 9 to 2. Clean buff. |
| Web | SKIP / TACTICS REMIX + ZSTWEAKS | Preserve the priority stack. |
| Agannazar's Scorcher | SKIP / MIXED + ZSTWEAKS | Useful SR range changes but altered damage timing; ZSTweaks also owns selected behavior. |
| Ghoul Touch | INCLUDE — ADAPTED | Import SR's +4 hit bonus, +1 effective enchantment, 1d8 magic damage and improved paralysis save, but retain vanilla casting time 1 instead of SR's 2. |
| Vocalize | SKIP / NO MATERIAL BUFF | No meaningful mechanical improvement. |
| Power Word Sleep | INCLUDE — ADAPTED | SR retains irresistible sleep at 1–19 HP and additionally allows 20+ HP targets to be affected on a failed save. Preserve vanilla Conjuration/Summoning school. |
| Ray of Enfeeblement | SKIP / MIXED + ZSTWEAKS | SR trades the vanilla Strength=5 effect for fixed combat penalties; ZSTweaks also touches the spell. |
| Chaos Shield | SKIP / NERF | Same surge bonus with generally shorter duration. |
| Sound Burst | ACCEPT REPLACEMENT — replaces Deafness | Full SR replacement. SPWI223/SCRLA2 become Sound Burst; Deafness is not kept separately. |
| Glitterdust | SKIP / MIXED | Better anti-invisibility reliability but loses vanilla's stronger save-or-blind effect. |
| Resist Elements | ADD AS NEW SPELL | New Level-2 Abjuration granting 25% resistance to all elemental damage. |
| Monster Summoning II | SKIP / DUPLICATE IWDIFICATION | Avoid a second same-name summoning spell; retain IWDification. |

## Final selected set

Existing spells buffed:
- Strength
- Ghoul Touch — SR mechanics with vanilla casting time 1
- Power Word Sleep — SR mechanics with vanilla Conjuration/Summoning school

Accepted replacements:
- Detect Alignment completely replaces Know Alignment and is moved to Level 1
- Battering Ram completely replaces Knock
- Sound Burst completely replaces Deafness

New spell:
- Resist Elements

Explicitly excluded:
- Know Opponent

## Technical replacement policy

### Detect Alignment / Know Alignment

The installer:
1. Resolves the pre-existing `WIZARD_KNOW_ALIGNMENT` resource before the move.
2. Uses SR's Level-1 Detect Alignment through `ADD_SPELL`, retaining the established `WIZARD_KNOW_ALIGNMENT` semantic identifier for compatibility and adding `WIZARD_DETECT_ALIGNMENT` as an alias.
3. Converts existing learnable Know Alignment scrolls to teach the new Level-1 Detect Alignment resource.
4. Replaces the old Know Alignment SPL with Detect Alignment mechanics as a compatibility alias for scripts/CREs that still reference the old numeric resource.
5. Hides that compatibility alias from normal EE spell-selection screens so the player does not get a second Level-2 copy.

### Battering Ram / Knock

Battering Ram directly occupies the vanilla Knock resource and scroll:
- `SPWI207`
- `SCRL91`

The original `WIZARD_KNOCK` symbol remains valid for compatibility, while `WIZARD_BATTERING_RAM` is added as a semantic alias.

### Sound Burst / Deafness

Sound Burst directly occupies the vanilla Deafness resource and scroll:
- `SPWI223`
- `SCRLA2`

The original `WIZARD_DEAFNESS` symbol remains valid for compatibility, while `WIZARD_SOUND_BURST` is added as a semantic alias.

## Scroll roadmap

No new distribution work is needed for the three replacements:
- Detect Alignment inherits converted Know Alignment scroll placements.
- Battering Ram inherits Knock scroll placements.
- Sound Burst inherits Deafness scroll placements.

Resist Elements is genuinely new. Its dedicated scroll resource is `DVRESSCR.ITM`; EET distribution remains deferred to the unified arcane scroll-distribution pass together with:
- Obscuring Mist
- Dimension Jump

## Status

**CLOSED for spell selection and implemented in component #0.**

Further Level-2 changes should be limited to technical fixes found during install/in-game testing or the deferred scroll-distribution pass.
