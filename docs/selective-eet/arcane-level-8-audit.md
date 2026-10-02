# Arcane Level 8 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks changes > IWDification > selected Spell Revisions v4.21 changes.

Spell Revisions v4.21 source is authoritative for SR behavior. Tactics Remix 8.2's mage-chess and physical-defense semantics remain higher priority.

| Spell | Decision | Reason |
|---|---|---|
| Ghostform | ADD AS NEW SPELL | Genuine SR Level-8 Alteration with no semantic duplicate found in ZSTweaks/IWDification. Grants incorporeal defenses, 50% physical resistance, AC 0, poison/disease immunity, anti-backstab, +100% Move Silently and touch-attack benefits. IWDification already occupies SPWI801 with Monster Summoning VI, so Ghostform must be dynamically allocated and use its own scroll. |
| Mind Blank | SKIP / IWDIFICATION | IWDification already supplies WIZARD_MIND_BLANK at SPWI802. Its version lasts 24 hours, casts in 1, and protects against charm, maze, feeblemind, confusion, fear, intoxication, berserk, hold and petrification. SR's touch-cast version lasts only 8 hours and casts in 8. Preserve the higher-priority IWDification spell. |
| Protection from Energy | INCLUDE | Clear SR upgrade: 75% -> 100% protection against acid, cold, electricity, fire and magic damage, and duration doubles from 1 round/level to 2 rounds/level. Core spell function is unchanged. |
| Simulacrum | SKIP / NO CLEAN BUFF | Same 60%-level/HP clone and same 1 round/level duration. SR changes casting time from vanilla 9 to 1 round and adds an explicit one-simulacrum limit. No meaningful favorable mechanic to import. |
| Pierce Shield | SKIP / TACTICS MAGE CHESS | Tactics Remix owns this resource and redefines Pierce Shield as an 8th-level anti-defense spell that removes Specific/Combat Protections and reduces physical damage resistance. Tactics also moves Pierce Magic to Level 8 to act as vanilla Pierce Shield. Do not overwrite either semantic. |
| Summon Fiend | SKIP / SUMMON-ASSET REWORK | SR's main changes are a custom Glabrezu CRE/AI/spellbook and a 3-turn duration. Avoid replacing summoned-creature assets in the Tactics/IWDification environment. |
| Improved Mantle / SR Moment of Prescience | KEEP TACTICS; MOMENT OPTIONAL AS NEW | Tactics directly owns Improved Mantle and upgrades its physical protection/resistance. SR replaces it with the unrelated Divination Moment of Prescience. Never overwrite Improved Mantle. Moment of Prescience can safely be registered as a separate new Level-8 spell if approved. |
| Spell Trigger / Simbul's Spell Trigger | INCLUDE — ADAPTED | Same core three-spells-of-Level-6-or-lower trigger. SR makes it Universal but uses 1-round casting instead of vanilla 9. Change only the school to Universal and clear specialist exclusions, preserving installed mechanics/casting time. |
| Incendiary Cloud | INCLUDE — ADAPTED | SR doubles area to 30 ft. and adds smoke penalties (-4 THAC0 and AC), but replaces vanilla's much stronger 1d4 damage/level with fixed 4d6 and changes Save vs. Spell to Breath. Keep vanilla scaling damage, Evocation school and Save vs. Spell; import SR's 30-ft. area and smoke penalties. Strict buff. |
| Symbol, Fear / SR Symbol of Weakness | KEEP SYMBOL FEAR; WEAKNESS OPTIONAL AS NEW | SR replaces Symbol Fear with a distinct ability-score debuff. This project should not remove the unique vanilla Symbol Fear. Symbol of Weakness can instead be added as a separate dynamically allocated Level-8 spell if approved. |
| Abi-Dalzim's Horrid Wilting | SKIP / ZSTWEAKS | ZSTweaks component 410 directly rebuilds Horrid Wilting's damage/target-type behavior. Preserve ZS. SR also lowers damage from vanilla 1d8/level to capped 1d6/level despite larger area/save penalty. |
| Maze | SKIP / ZSTWEAKS | ZSTweaks component 405 directly patches Maze's immunity/interaction behavior. Preserve ZS. |
| Power Word Blind | INCLUDE — ADAPTED | Vanilla is a 4-ft. no-save AoE lasting 6 rounds. SR is single-target but lasts 1 turn and permanently blinds targets below 6 HD. Keep vanilla Conjuration/Summoning school and 4-ft. AoE, extend normal duration to 1 turn, and add SR's permanent-blindness rule for <6-HD targets. Strict buff. |
| Symbol, Stun | INCLUDE — ADAPTED | SR expands area from 12 ft. to 20 ft. but fixes stun duration at 4 rounds, much shorter than vanilla's 2 rounds + 1 round/3 levels at normal Level-8 caster levels. Keep vanilla scaling duration and casting time 9; import SR's 20-ft. area/trigger coverage. |
| Symbol, Death | INCLUDE — ADAPTED | SR expands area from 12 ft. to 20 ft. and adds a -4 Save vs. Death penalty while retaining the 60-current-HP cap. Keep vanilla casting time 9; import the larger area and -4 save penalty. Strict buff. |
| Bigby's Clenched Fist / SR Bigby's Icy Grasp | KEEP ZSTWEAKS; ICY GRASP OPTIONAL AS NEW | ZSTweaks component 445 directly and substantially buffs Bigby's Clenched Fist. Preserve that higher-priority version. SR's Icy Grasp can technically be added as a separate dynamic Level-8 spell if approved, without touching Clenched Fist. |
| Monster Summoning VIII / WIZARD_MONSTER_SUMMONING_6 | SKIP / DUPLICATE IWDIFICATION | IWDification already owns WIZARD_MONSTER_SUMMONING_6 at Level 8/SPWI801 as Monster Summoning VI, integrated into its IWD summoning progression. Retain IWDification. |

## Proposed selected set

### INCLUDE
- Protection from Energy — full SR upgrade

### INCLUDE — ADAPTED
- Spell Trigger — Universal school only
- Incendiary Cloud — vanilla damage/save/school + SR 30-ft. area and smoke penalties
- Power Word Blind — vanilla 4-ft. AoE/school + SR 1-turn duration and permanent blindness for targets below 6 HD
- Symbol, Stun — vanilla scaling stun duration/casting time + SR 20-ft. area
- Symbol, Death — vanilla casting time + SR 20-ft. area and -4 Save vs. Death

### ADD AS NEW SPELL
- Ghostform — dynamically allocated Level-8 spell because IWDification owns SPWI801

Everything else remains with vanilla, Tactics Remix, ZSTweaks or IWDification.

## Replacement-to-addition candidates requiring explicit approval

### Moment of Prescience
Keep Tactics Improved Mantle completely intact and add SR's Moment of Prescience as a separate dynamic Level-8 Divination:
- Casting Time 1
- Duration 4 rounds
- +20 AC
- +20 to all saving throws

No WIZARD_MOMENT_OF_PRESCIENCE conflict was found in IWDification or ZSTweaks.

### Symbol of Weakness
Keep Symbol Fear completely intact and add SR Symbol of Weakness as a separate dynamic Level-8 Conjuration:
- 20-ft. area
- Save vs. Spell at -4
- -4 Strength, Dexterity and Constitution
- persists until Cure Disease

No WIZARD_SYMBOL_WEAKNESS conflict was found in IWDification or ZSTweaks.

### Bigby's Icy Grasp
Keep the ZSTweaks-enhanced Bigby's Clenched Fist completely intact and add SR Bigby's Icy Grasp separately:
- Long range
- 8-round duration
- 2d8 cold damage each round
- Save vs. Breath at -2 each round or held for 1 round

No WIZARD_BIGBYS_ICY_GRASP conflict was found in IWDification or ZSTweaks. Because it is mechanically close to Clenched Fist, it is left optional rather than selected automatically.

## Priority-mod notes

### Tactics Remix 8.2
Level-8 mage-chess/physical-defense semantics that must remain untouched:
- Pierce Shield removes Specific and Combat Protections and reduces physical damage resistance.
- Pierce Magic is moved to Level 8 and acts as vanilla Pierce Shield.
- Improved Mantle is directly strengthened by the physical-defense overhaul (+40% physical resistance and one higher enchantment tier of weapon protection in the relevant component).
- Tactics scripts are explicitly written for vanilla/Tactics spell semantics, not full Spell Revisions replacements.

Therefore Pierce Shield and Improved Mantle are never overwritten.

### ZSTweaks
Relevant enabled Level-8 overlaps:
- 405 — Maze
- 410 — Abi-Dalzim's Horrid Wilting
- 445 — Bigby's Clenched Fist / Crushing Hand

These are preserved. The user previously disabled the unrelated Flesh to Stone / Stone to Flesh tweak (#444); it does not affect this Level-8 audit.

### IWDification
Relevant ownership:
- SPWI801 = WIZARD_MONSTER_SUMMONING_6 (Monster Summoning VI)
- SPWI802 = WIZARD_MIND_BLANK
- IWDification also contains the standard Level-8 spell IDs/resources and integrates Mind Blank with its own fixes.
- Its Monster Summoning VI belongs to the established IWD summoning progression and must not be replaced by SR Monster Summoning VIII.

Therefore Ghostform must be dynamically allocated and SR Mind Blank / Monster Summoning VIII are not imported.

## Scroll implications

In-place proposed changes inherit existing scroll distribution:
- Protection from Energy
- Spell Trigger
- Incendiary Cloud
- Power Word Blind
- Symbol, Stun
- Symbol, Death

Ghostform is genuinely new and needs a unique learnable scroll plus dynamic EET distribution.

If approved as separate spells, Moment of Prescience, Symbol of Weakness and Bigby's Icy Grasp will each also require a unique scroll and dynamic EET distribution because their original SR implementation consumes/replaces an existing vanilla spell slot/scroll.

The deferred new-scroll list would therefore contain at minimum:
- Obscuring Mist
- Dimension Jump
- Resist Elements
- Protection from Elemental Energy
- Mestil's Acid Sheath
- Banishment
- Summon Death Knight
- Ghostform

## Status

**OPEN — awaiting user approval of the proposed Level-8 selection and explicit decisions on Moment of Prescience, Symbol of Weakness and Bigby's Icy Grasp before implementation in component #0.**
