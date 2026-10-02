# Arcane Level 7 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks changes > IWDification > selected Spell Revisions v4.21 changes.

Spell Revisions v4.21 source is authoritative for SR behavior. Tactics Remix 8.2's mage-chess and physical-defense semantics remain higher priority.

| Spell | Decision | Reason |
|---|---|---|
| Spell Turning / SR Greater Spell Deflection | SKIP / TACTICS MAGE CHESS + REPLACEMENT | SR changes reflection into absorption and renames the spell Greater Spell Deflection. Tactics explicitly uses Spell Turning as a distinct protection type, including interaction with Breach. Preserve Tactics/vanilla Spell Turning. |
| Protection from the Elements | INCLUDE | SR is a clear upgrade: resistance rises from 75% to 100% and duration increases from vanilla 1 round/level to 1 turn per 2 levels. Core function remains the same and no higher-priority overlap was found. |
| Project Image | SKIP / SYSTEM-COUPLED REWORK | SR adds concealment/invisibility to the caster and changes the surrounding illusion/True Seeing model through auxiliary resources. This is beneficial in isolation but coupled to SR's broader illusion system and can alter AI assumptions. Keep installed Project Image. |
| Ruby Ray of Reversal | INCLUDE — ADAPTED | SR increases range from vanilla 40 ft. to Long, but its protection-removal list is rewritten around the SR protection ladder and omits vanilla/Tactics protections that remain in this project. Preserve the installed removal behavior/list and import only the longer SR range. |
| Khelben's Warding Whip | SKIP / TACTICS MAGE CHESS | Tactics Remix moves Khelben's Warding Whip to arcane Level 6 and uses it in its own anti-magic hierarchy. Do not restore/overwrite the Level-7 SR resource. |
| Cacofiend / SR Summon Death Knight | SKIP / REPLACEMENT + SUMMON ASSET RISK | SR completely replaces Cacofiend with a custom Death Knight summon. This removes an existing spell and introduces a custom summoned creature outside the Tactics/IWDification summon hierarchy. Keep Cacofiend. A standalone Death Knight spell is technically possible later, but is not included by default. |
| Mantle / SR Prismatic Mantle | SKIP / TACTICS REMIX | Tactics' physical-defense overhaul directly improves Mantle and its enchantment/physical-resistance behavior. SR's Prismatic Mantle is a different spell entirely. Preserve Tactics Mantle. |
| Spell Sequencer / Simbul's Spell Sequencer | INCLUDE — ADAPTED | SR makes the spell Universal, allowing all specialist mages to use it, but its 1-round casting time is not an improvement over vanilla casting time 9. Change only the school to Universal and clear specialist exclusions; keep installed sequencer mechanics/casting time. |
| Sphere of Chaos / SR Chaos | SKIP / REPLACEMENT + DUPLICATE ROLE | This project deliberately retained vanilla Chaos at Level 5. SR replaces Sphere of Chaos with another Chaos spell at Level 7, creating a duplicate role/name and removing the unique Sphere spell. Keep Sphere of Chaos. |
| Delayed Blast Fireball | INCLUDE — ADAPTED | SR greatly increases radius (11 ft. -> 30 ft.), trigger radius, range, late-game damage scaling (up to 20d6) and applies a -4 save penalty, but changes Save vs. Spell to Save vs. Breath and is 1d6 weaker at caster level 14. Use a strict-buff hybrid: retain Save vs. Spell; use 15d6 minimum at levels 14-15, then scale 1d6/level to 20d6; apply SR's -4 save penalty, Long range and 30-ft. blast. |
| Finger of Death | SKIP / ZSTWEAKS | ZSTweaks component 140 directly standardizes/improves Finger of Death and its damage scaling. Preserve ZS. |
| Prismatic Spray | SKIP / MIXED | SR gives casting time 1 and -4 saves, but substantially changes the ray outcomes: the yellow damage ray can be much weaker than vanilla, petrification becomes stun, and disintegration becomes Maze. Major redesign rather than a strict buff. |
| Power Word Stun | INCLUDE — ADAPTED | Vanilla does nothing to targets at 90+ current HP; SR stuns such targets for 1 round while leaving all lower-HP duration bands intact. Add only the 1-round 90+ HP band and preserve vanilla Conjuration/Summoning school. Strict buff. |
| Mordenkainen's Sword | SKIP / IWDIFICATION + SUMMON ASSET REWORK | IWDification supplies/normalizes its own IWD Mordenkainen's Sword implementation and related force-blade resources. SR also replaces the summoned sword creature/item/stat package. Preserve IWDification. |
| Summon Efreeti | SKIP / SUMMON ASSET REWORK | Duration is effectively unchanged, while SR's main change is a custom stronger genie CRE/spellbook/AI package. Avoid replacing summon assets in the Tactics/IWDification environment. |
| Summon Djinni | INCLUDE — ADAPTED | SR increases duration from vanilla 1 round/level to 8 rounds + 1 round/level. Import only this duration improvement and retain the installed Djinni creature/resources. |
| Summon Hakeashar / SR Nishruu-Hakeashar rework | SKIP / SUMMON REWORK | SR reorganizes Nishruu/Hakeashar progression and summon assets. This project already kept Summon Nishruu at Level 6 rather than accepting SR's level shift. Preserve the installed Level-7 Hakeashar spell. |
| Control Undead | SKIP / ZSTWEAKS | ZSTweaks component 500 already makes Control Undead bypass Magic Resistance and applies a -2 saving-throw penalty. Preserve ZS rather than replacing it with SR's separate HD/caster-level formula. |
| Mass Invisibility | INCLUDE — ADAPTED | SR doubles the area from 15 ft. to 30 ft. ZSTweaks True Sight compatibility also patches SPWI721 in the established project setup, so patch only the installed spell's area/projectile and preserve all ZS invisibility effects and vanilla Improved Invisibility semantics. |
| Limited Wish | INCLUDE — ADAPTED | SR makes Limited Wish Universal, removing the vanilla specialist exclusions, while the underlying wish dialogue/mechanics need not be replaced. Change only the school to Universal and clear specialist exclusions, preserving ZSTweaks' Limited-Wish-specific Wail interaction. |
| Improved Chaos Shield | SKIP / NERF | Wild-surge bonus remains +25, but SR cuts duration from vanilla 2 hours to 2 turns. Keep vanilla. |
| SR Monster Summoning VII / WIZARD_MONSTER_SUMMONING_5 | SKIP / DUPLICATE IWDIFICATION | IWDification already supplies WIZARD_MONSTER_SUMMONING_5 as its coherent Level-7 Monster Summoning V, with summon assets and scroll distribution. Retain IWDification. |

## Proposed selected set

### INCLUDE
- Protection from the Elements — full SR upgrade (100% elemental resistance and longer duration)

### INCLUDE — ADAPTED
- Ruby Ray of Reversal — longer SR range only; retain installed/Tactics protection-removal list
- Spell Sequencer — Universal school only; retain installed mechanics and casting time
- Delayed Blast Fireball — 15d6 minimum, scales to 20d6; 30-ft. SR area/Long range/-4 Save vs. Spell
- Power Word Stun — add SR's 1-round effect against targets with 90+ current HP; retain vanilla school
- Summon Djinni — SR duration improvement only; retain installed summon assets
- Mass Invisibility — SR 30-ft. area only; preserve ZSTweaks/vanilla invisibility behavior
- Limited Wish — Universal school only; preserve existing Wish dialogue/options and ZSTweaks interactions

### ADD AS NEW SPELL
- Summon Death Knight — dynamically allocated Level-7 spell; Cacofiend remains untouched

Everything else remains with vanilla, Tactics Remix, ZSTweaks or IWDification.

## Additional new spell

### Summon Death Knight
User-approved as a separate new Level-7 spell. Cacofiend remains fully intact. The implementation dynamically allocates the new spell, copies SR's Death Knight CRE/ITM/BCS assets, copies SR's SPCACO.EFF under the private resource `DVDKTEFF.EFF`, and retargets only the new spell to that private EFF. The dedicated learnable scroll is `DVDKSCR.ITM`.

### Prismatic Mantle
Not selected. Tactics deliberately owns the physical-defense spell hierarchy and Prismatic Mantle would add another high-level defensive option outside that balance.

## Priority-mod notes

### Tactics Remix 8.2
Relevant Level-7 semantics:
- Breach is blocked by Spell Deflection, Spell Turning and Spell Trap, making reflection/deflection distinctions part of the Tactics mage-chess model.
- Rakshasa remain immune to Level-7-and-lower spells, explicitly including Ruby Ray and Khelben's Warding Whip.
- Khelben's Warding Whip is moved to Level 6.
- Mantle is directly improved by the physical-defense overhaul (+40% physical resistance and one higher enchantment tier of weapon protection in the relevant component).

Therefore Spell Turning, Khelben's Warding Whip and Mantle are not replaced by SR.

### ZSTweaks
Relevant established Level-7 overlaps:
- 140 — Finger of Death standardization/damage scaling
- 500 — Control Undead bypasses Magic Resistance and gains a -2 save penalty
- 582 — True Sight/invisibility compatibility patches Mass Invisibility; the selective module must preserve those existing effects
- the Wail of the Banshee tweak can alter the one-time Limited Wish version; changing Limited Wish to Universal must not overwrite that dialogue/spell interaction

### IWDification
Relevant ownership:
- WIZARD_MONSTER_SUMMONING_5 is already supplied at Level 7 with its own summon progression and scroll placement.
- IWDification has its own Mordenkainen's Sword / force-blade implementation and post-processing.
- Existing genie and Hakeashar resources are left untouched by the proposed duration-only Djinni patch.

## Scroll implications

All proposed Level-7 changes are in-place revisions of existing spells:
- Protection from the Elements
- Ruby Ray of Reversal
- Spell Sequencer
- Delayed Blast Fireball
- Power Word Stun
- Summon Djinni
- Mass Invisibility
- Limited Wish

No new Level-7 scroll resource or distribution work is required for the proposed set.

Summon Death Knight is genuinely new and uses the dedicated scroll resource `DVDKSCR.ITM`. Cacofiend and its original scroll remain untouched. `DVDKSCR.ITM` must be distributed dynamically during the unified EET arcane-scroll pass.

The deferred new-scroll list now includes:
- Obscuring Mist
- Dimension Jump
- Resist Elements
- Protection from Elemental Energy
- Mestil's Acid Sheath
- Banishment
- Summon Death Knight

## Status

**CLOSED for spell selection and implemented in component #0.**

Further Level-7 changes should be limited to technical fixes found during install/in-game testing or the deferred scroll-distribution pass.
