# Arcane Level 5 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks changes > IWDification > selected Spell Revisions v4.21 changes.

Spell Revisions v4.21 source is authoritative for SR behavior. Tactics Remix 8.2 spell-system documentation is used to preserve its mage-chess semantics and Spell Tweaks behavior.

| Spell | Decision | Reason |
|---|---|---|
| Animate Dead / SR Summon Shadow | SKIP / DUPLICATE IWDIFICATION | SR replaces Animate Dead with Summon Shadow. IWDification already adds Summon Shadow as a separate Level-5 spell and distributes its scroll, while leaving Animate Dead available. Replacing Animate Dead would remove a vanilla spell and create a semantic duplicate. |
| Cloudkill | SKIP / TACTICS REMIX | Tactics Remix Spell Tweaks explicitly changes Cloudkill to 1d4 poison damage per round. Preserve the Tactics version rather than overwriting it with SR's larger 30-ft. cloud and different damage handling. |
| Cone of Cold | SKIP / TACTICS REMIX | Tactics Remix directly revises Cone of Cold: it retains the strong scaling (up to 20d4+20) and adds a 50% movement-rate penalty on failed saves. SR instead caps at 15d4+15 and changes cone/save/casting behavior. Preserve Tactics. |
| Monster Summoning III / SR Monster Summoning V | SKIP / IWDIFICATION | IWDification owns WIZARD_MONSTER_SUMMONING_3 / SPWI504 as the Level-5 step of its coherent IWD Monster Summoning progression. Do not replace it with SR's differently named Monster Summoning V. |
| Shadow Door | SKIP / ZSTWEAKS | ZSTweaks component 582 directly patches SPWI505 so invisibility cannot be reapplied while True Sight is active. SR adds a strong extradimensional-trap effect, but copying SR wholesale would erase the higher-priority ZS patch. Preserve ZS. |
| Domination | INCLUDE — ADAPTED | SR extends duration from vanilla 8 rounds to 1 turn without changing the core domination/save behavior. Patch the installed spell's duration only, preserving all other installed semantics/resources. |
| Hold Monster | INCLUDE — ADAPTED | SR expands the splash radius from 4 ft. to 5 ft. but changes vanilla's 1 round/level duration to a fixed 1 turn. Import only the larger SR area while retaining vanilla's scaling duration and -2 Spell save. |
| Chaos / SR Waves of Fatigue | SKIP / TACTICS SEMANTICS + REPLACEMENT | SR completely replaces Chaos with a no-save fatigue effect. Tactics Remix explicitly warns that its scripts are written around vanilla/Tactics spell semantics; enemy AI using WIZARD_CHAOS expects the confusion spell. Keep Chaos. |
| Feeblemind | INCLUDE — ADAPTED | SR improves the save penalty from vanilla -2 to -4 while retaining the permanent feeblemind effect. Import the stronger save penalty without otherwise replacing the installed spell. |
| Spell Immunity / SR Dispelling Screen | SKIP / TACTICS MAGE CHESS | Spell Immunity is part of the vanilla/Tactics protection vocabulary used by Tactics mage-chess logic. Dispelling Screen is a fundamentally different SR replacement. Preserve Spell Immunity. |
| Protection from Normal Weapons | SKIP / TACTICS REMIX + NERF | Tactics Remix's physical-defense overhaul adds 20% physical damage resistance while retaining casting time 2. SR uses casting time 5 and offers no compensating benefit needed here. |
| Protection from Electricity | KEEP EXISTING / REDUNDANT LEVEL SHIFT | SR effectively moves this 100% protection spell to Level 4. This project already adds the more flexible Protection from Elemental Energy at Level 4, so moving the individual spell down a level only adds redundancy and spellbook clutter. |
| Breach | SKIP / TACTICS MAGE CHESS | Tactics Remix changes the mage-chess rules around Breach, including interaction with spell deflection/turning/trap and creature spell-level immunities. Do not replace the spell with SR's protection list. |
| Lower Resistance | INCLUDE — ADAPTED | Vanilla lowers MR by 10% + 1%/level; SR uses 2%/level, capped at 40%. SR is 1 point weaker at caster level 9, equal at level 10, and stronger thereafter. Use the better-of-both progression: preserve 19% at level 9, then use SR's 2%/level from level 10 onward (up to 40%), retaining the existing school and semantics. |
| Oracle | INCLUDE — ADAPTED | SR expands the set of removable illusions (including Blur, Ghost Armor, Invisibility Sphere, Mislead, Project Image, Pixie Dust and Mass Invisibility), but cuts the radius from vanilla 120 ft. to 30 ft. and omits Non-Detection. Keep vanilla 120-ft. radius and Non-Detection removal, while adding SR's expanded illusion coverage. Strict buff. |
| Conjure Lesser Fire Elemental | SKIP / IWDIFICATION | IWDification owns and normalizes the Lesser Elemental spell family, including Fire, Air, Earth and Water, and explicitly marks the SR elemental variants as duplicates to skip. Preserve the IWDification set. |
| Protection from Acid | KEEP EXISTING / REDUNDANT LEVEL SHIFT | Like Protection from Electricity, SR moves the individual 100% protection spell to Level 4. Protection from Elemental Energy already supplies selectable 100% acid protection at Level 4, so retain the existing Level-5 spell. |
| Phantom Blade | SKIP / MIXED | SR raises enchantment and adds touch-attack/spell-disruption benefits, but shortens duration and removes Strength-based damage contribution. ZSTweaks also contains a Phantom Blade damage compatibility fix. Not a clean upgrade. |
| Spell Shield | SKIP / TACTICS MAGE CHESS + MIXED | SR improves casting time but changes the protection list and omits vanilla protection against Breach and Lower Resistance. Tactics' mage-chess system also treats Spell Shield as part of its protection vocabulary. Preserve the installed version. |
| Conjure Lesser Air Elemental | SKIP / IWDIFICATION | Preserve IWDification's coherent four-element Lesser Elemental family. |
| Conjure Lesser Earth Elemental | SKIP / IWDIFICATION | Preserve IWDification's coherent four-element Lesser Elemental family. |
| Minor Spell Turning / SR Spell Deflection | SKIP / TACTICS SEMANTICS + MIXED | SR replaces reflection with absorption and increases capacity. This is not a strict buff, and it changes a core mage-chess protection type used by Tactics. Keep Minor Spell Turning. |
| Sunfire / SR Fireburst | SKIP / ZSTWEAKS | ZSTweaks component 446 directly improves Sunfire's damage scaling. SR renames/reworks it as Fireburst with different save/casting behavior. Preserve ZS. |
| Mestil's Acid Sheath | ADD AS NEW SPELL | Useful new Level-5 Conjuration: 50% acid resistance plus 4d4 acid retaliation against attacks/spells made from within 5 ft., lasting 2 turns. No equivalent spell is supplied by IWDification or the selected ZSTweaks/Tactics spell tweaks. Must be dynamically allocated because IWDification already uses SPWI526 for Summon Shadow. |

## Final selected set

### INCLUDE — ADAPTED
- Domination — duration extended to 1 turn while preserving the installed spell's behavior
- Hold Monster — SR 5-ft. splash radius with vanilla 1 round/level duration retained
- Feeblemind — Save vs. Spell penalty improved from -2 to -4
- Lower Resistance — vanilla Abjuration school and 40-ft. range retained; 19% at caster level 9, then SR's 2%/level progression from level 10 onward, capped at 40%
- Oracle — vanilla 120-ft. radius and Non-Detection removal retained, with SR's expanded illusion-removal list added

### ADD AS NEW SPELL
- Mestil's Acid Sheath — dynamically allocated Level-5 spell with an independent retaliation subspell

Everything else stays with vanilla, Tactics Remix, ZSTweaks or IWDification.

## Priority-mod notes

### Tactics Remix 8.2
Relevant Level-5 interactions:
- Cloudkill: Spell Tweaks reduces recurring poison damage to 1d4.
- Cone of Cold: Spell Tweaks adds a movement penalty and retains stronger high-level scaling.
- Protection from Normal Weapons: the physical-defense overhaul adds 20% physical damage resistance.
- Breach and the broader protection-removal system are part of Tactics' mage-chess rules.
- Tactics explicitly states that its scripts assume vanilla/Tactics spell semantics; complete SR replacements can cause AI inconsistencies. For that reason Chaos, Spell Immunity and Minor Spell Turning are not replaced.

### ZSTweaks
Relevant Level-5 interactions:
- 582 — patches Shadow Door and other invisibility sources for True Sight compatibility.
- 446 — directly improves Sunfire scaling.
- Phantom Blade has an additional ZSTweaks compatibility/fix path; SR's mixed redesign is therefore not imported.

### IWDification
Relevant Level-5 ownership:
- SPWI504 = WIZARD_MONSTER_SUMMONING_3
- SPWI526 = WIZARD_SUMMON_SHADOW
- IWDification owns the Lesser Fire/Air/Earth Elemental implementations and adds Lesser Water Elemental as part of the same family.
- Its compatibility data explicitly identifies SR Summon Shadow and SR Lesser Elementals as duplicates to skip.

## Scroll implications

All adapted existing spells inherit their current scroll distribution:
- Domination
- Hold Monster
- Feeblemind
- Lower Resistance
- Oracle

Mestil's Acid Sheath is genuinely new. Upstream SR reuses the Fire Shield (Blue) scroll because SR repurposes that spell; this project keeps Fire Shield (Blue) for Tactics compatibility. The implemented spell therefore uses the dedicated learnable scroll resource `DVMASSCR.ITM`, which must be distributed dynamically during the unified EET arcane-scroll pass. Fire Shield (Blue) and its scroll remain untouched.

Deferred new-scroll list would become:
- Obscuring Mist
- Dimension Jump
- Resist Elements
- Protection from Elemental Energy
- Mestil's Acid Sheath

## Status

**CLOSED for spell selection and implemented in component #0.**

Further Level-5 changes should be limited to technical fixes found during install/in-game testing or the deferred scroll-distribution pass.
