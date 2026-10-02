# Arcane Level 9 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks changes > IWDification > selected Spell Revisions v4.21 changes.

Spell Revisions v4.21 source is authoritative for SR behavior. Tactics Remix 8.2's mage-chess/physical-defense semantics and the enabled ZSTweaks arcane components remain higher priority.

| Spell | Decision | Reason |
|---|---|---|
| Spell Trap | SKIP / TACTICS MAGE CHESS + MIXED SR REWORK | Tactics mage AI explicitly tracks Spell Trap as a distinct spell-protection state. SR changes the spell from vanilla/Tactics 30 absorbed spell levels with spell-slot recall into a 99-level absorber without the vanilla recall behavior, and also changes duration handling. This is a major semantic redesign rather than a clean buff. Preserve the installed Spell Trap. |
| Spellstrike | SKIP / TACTICS DIRECT PATCH | Tactics Remix directly patches SPWI903 so its anti-magic effects use power 10 and can take down Protection from Magic scroll defenses. SR also rewrites the protection list and adds 100% spell failure for 1 round followed by 50% for another round. Copying SR would overwrite the higher-priority Tactics implementation. |
| Gate | SKIP / TACTICS DEMON HIERARCHY + MIXED | SR replaces the summoned Pit Fiend CRE/AI/spellbook with its own custom creature and shortens duration from vanilla 33 rounds to 3 turns. Tactics Remix has extensive Pit Fiend/demon scripting and creature modifications, including dempit/dempitsu. Do not overwrite that hierarchy with SR assets. |
| Absolute Immunity | SKIP / TACTICS DIRECT PATCH | Tactics directly rebuilds SPWI907 as complete weapon immunity plus 40% physical damage resistance and integrates it into its physical-defense ladder. SR instead grants complete physical and magical damage immunity. Despite being stronger, it would override the top-priority Tactics balance/semantics. |
| Chain Contingency | INCLUDE — ADAPTED | SR makes Chain Contingency Universal, removing opposition-school restrictions, but uses casting time 1 round instead of vanilla 9. Change only the school to Universal and clear specialist exclusions; preserve installed mechanics and casting time. |
| Time Stop | SKIP / NO MATERIAL BUFF | Core effect remains three rounds of stopped time. SR's listed casting time is 1 round, which is slightly worse than vanilla casting time 9, and there is no clean mechanic worth importing. |
| Imprisonment | SKIP / ZSTWEAKS | ZSTweaks component 562 directly patches Imprisonment/Maze interaction. SR adds short range but changes casting time from 9 to 1 round and carries its own imprisonment framework. Preserve ZS. |
| Meteor Swarm | SKIP / ZSTWEAKS | ZSTweaks component 180 directly rebuilds Meteor Swarm damage/scaling and its Wish counterpart. Preserve ZS. |
| Power Word Kill | SKIP / ZSTWEAKS | ZSTweaks component 585 directly rebuilds Power Word Kill, including HP/HD logic, death handling, optional MR bypass and school handling. Preserve ZS. |
| Wail of the Banshee | SKIP / ZSTWEAKS | ZSTweaks component 170 directly rebuilds Wail of the Banshee, including HD/HP handling, save penalties, survivor damage/debuff and Limited Wish interaction. Preserve ZS. |
| Energy Drain / SR Larloch's Energy Drain | SKIP / ZSTWEAKS | ZSTweaks component 400 directly rebuilds Energy Drain and its Wish counterpart, including 4-level drain logic and target-type handling. SR's 4-level drain plus self-buff redesign would overwrite the higher-priority ZS implementation. |
| Black Blade of Disaster | SKIP / ZSTWEAKS + MIXED | ZSTweaks component 160 patches the Black Blade item. SR changes school, casting time, proficiency/THAC0 behavior, disintegration chance/save and removes vanilla's 10% 4-level-drain + 20-HP heal proc. This is not a clean buff and would overwrite the ZS-touched blade assets. |
| Shapechange | SKIP / MIXED | SR cuts duration from 1 hour to 5 turns and removes the vanilla Earth Elemental and Fire Elemental forms, replacing the vanilla giant troll with Spirit Troll while heavily rebalancing all forms. Tactics AI also actively uses WIZARD_SHAPECHANGE. Major redesign, not a strict improvement. |
| Freedom | INCLUDE — ADAPTED | SR preserves the vanilla ability to free creatures from Maze and Imprisonment but additionally frees friendly creatures from charm, confusion, domination, entangle, feeblemind, hold, paralysis, petrification, sleep, slow, stun and web. Keep vanilla casting time 9 rather than SR's 1 round. This produces a strict utility buff without removing any vanilla function. |
| Bigby's Crushing Hand | SKIP / ZSTWEAKS | ZSTweaks component 445 directly and substantially improves Bigby's Crushing Hand, including MR bypass, stronger save penalties and higher damage. Preserve ZS. |
| Wish | KEEP EXISTING | Vanilla already belongs to Any School/Universal in practice. SR provides no clean main-spell buff, while Tactics patches Wish's Mass Breach subspell (SPWISH38) as part of mage chess and ZSTweaks patches several Wish outcomes. Preserve the installed Wish ecosystem unchanged. |
| SR Monster Summoning IX | SKIP / DISABLED SR SOURCE + IWDIFICATION | SR's Monster Summoning IX ADD_SPELL block is commented out in v4.21. IWDification already owns WIZARD_MONSTER_SUMMONING_7 / SPWI901 as its coherent Level-9 Monster Summoning VII with scroll distribution. Do not revive the disabled SR spell or collide with IWDification. |

## Final selected set

### INCLUDE — ADAPTED
- Chain Contingency — Universal school only; installed mechanics and casting time 9 retained
- Freedom — SR expanded mass-freedom/cure effects while retaining vanilla Maze/Imprisonment release and casting time 9

Everything else remains with vanilla, Tactics Remix, ZSTweaks or IWDification.

## Priority-mod notes

### Tactics Remix 8.2
Relevant Level-9 interactions verified from the supplied 8.2 package:
- SPWI903 Spellstrike is directly patched so anti-magic effects use power 10 and can defeat Protection from Magic scroll defenses.
- SPWI907 Absolute Immunity is directly rebuilt as complete weapon immunity plus 40% physical damage resistance and is part of Tactics' physical-defense ladder.
- Tactics mage scripts explicitly track WIZARD_SPELL_TRAP as a protection state.
- Tactics patches SPWISH38 (Wish Mass Breach) as part of the mage-chess Breach system.
- Tactics extensively modifies Pit Fiend/demon creatures and scripts used around Gate.

Therefore Spell Trap, Spellstrike, Gate, Absolute Immunity and the Wish anti-magic ecosystem are not overwritten by SR.

### ZSTweaks
Relevant enabled/group Level-9 overlaps:
- 160 — Black Blade of Disaster item/backstab handling
- 170 — Wail of the Banshee
- 180 — Meteor Swarm
- 400 — Energy Drain
- 445 — Bigby's Crushing Hand
- 562 — Imprisonment
- 585 — Power Word Kill

These resources remain owned by ZSTweaks. The user's previously disabled component #444 (Flesh to Stone / Stone to Flesh) is unrelated to Level 9.

### IWDification
Relevant ownership:
- SPWI901 = WIZARD_MONSTER_SUMMONING_7 (Monster Summoning VII)
- IWDification distributes its Level-9 Monster Summoning scroll as part of the IWD summoning progression.
- SR's Monster Summoning IX implementation is commented out in v4.21 anyway.

## Scroll implications

Both proposed Level-9 changes are in-place revisions:
- Chain Contingency
- Freedom

No new Level-9 scroll resource or distribution work is required.

The deferred new-scroll list remains:
- Obscuring Mist
- Dimension Jump
- Resist Elements
- Protection from Elemental Energy
- Mestil's Acid Sheath
- Banishment
- Summon Death Knight
- Ghostform

## Status

**CLOSED for spell selection and implemented in component #0.**

Further Level-9 changes should be limited to technical fixes found during install/in-game testing.
