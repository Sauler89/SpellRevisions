# Arcane Level 3 Audit — Selective Spell Revisions for EET

Priority model: Tactics Remix > enabled ZSTweaks spell tweaks > IWDification > selected Spell Revisions v4.21 changes.

Spell Revisions v4.21 source is authoritative when it differs from the older public documentation.

| Spell | Decision | Reason |
|---|---|---|
| Clairvoyance | ACCEPT REPLACEMENT | User-approved full SR replacement. The vanilla map-reveal utility is replaced by SR's 2-turn, non-dispellable defensive divination granting immunity to surprise/backstab and +2 AC / saves vs. Breath. |
| Remove Magic | SKIP / TACTICS REMIX | Tactics Remix has a dedicated Remove/Dispel Magic cast-level component and its AI is built around that behavior. Do not overwrite it with SR. |
| Flame Arrow | SKIP / MIXED | SR gains rapid missile scaling and can spread extra arrows among opponents, but each missile is much weaker than vanilla and SR caps at five arrows. At higher levels vanilla has substantially higher focused damage. |
| Fireball | SKIP / ZSTWEAKS | ZSTweaks component 446 deliberately improves Fireball-type damage scaling and/or visuals. Preserve ZS. SR is also a buff over vanilla (larger radius/range and -2 Breath save), but ZS has priority. |
| Haste | SKIP / ZSTWEAKS | ZSTweaks component 577 deliberately rebalances Haste/Improved Haste durations. SR also changes APR, speed, duration and adds a post-Haste winded penalty, so it must not overwrite ZS. |
| Hold Person | INCLUDE — ADAPTED | SR improves the save from -1 to -2 and slightly increases the splash radius from 4 ft. to 5 ft., with the same 1-turn duration. The only clear nerf is casting time 5 instead of vanilla 3. Import SR mechanics but retain vanilla casting time 3. |
| Invisibility Sphere | SKIP / MIXED | SR improves casting time from 9 to 1, but cuts the potential duration from 24 hours to 1 turn. Not a pure buff. |
| Lightning Bolt | SKIP / MIXED | SR becomes a safe single-target bolt with a strong -4 Breath save penalty, but loses vanilla's line/bounce multi-target behavior. Useful redesign, not a pure buff. |
| Monster Summoning I / SR Monster Summoning III | SKIP / IWDIFICATION STRUCTURAL CONFLICT | IWDification owns WIZARD_MONSTER_SUMMONING_1 / SPWI309 as its Level-3 Monster Summoning I and continues the IWD series with II at Level 4 and III at Level 5. SR repurposes that same slot as Monster Summoning III. Even though SR summons are strong, importing it would break the IWDification naming/progression we prioritize. |
| Non-Detection | SKIP / MIXED | SR rewrites the protection around anti-invisibility divinations and thief Detect Illusion rather than retaining all of vanilla's broader divination-protection semantics. Not a straight buff. |
| Protection from Normal Missiles / Protection from Missiles | SKIP / MIXED | SR expands protection to magical/conjured missiles as well as mundane projectiles, but reduces duration from 1 hour to 1 turn. The stronger coverage is balanced by a major duration loss. |
| Slow | SKIP / MIXED | SR doubles the area and adds casting-time/regeneration/poison interactions, but weakens vanilla's -4 AC/THAC0 and -4 save pressure to -2 values and changes the save type. |
| Skull Trap | SKIP / TACTICS REMIX | Tactics Remix Spell Tweaks owns Skull Trap and caps it at 12d6. SR caps at 10d6 and substantially changes radius/trigger/save behavior. Preserve Tactics. |
| Vampiric Touch | SKIP / MIXED | SR changes random 1d6/2 levels into fixed 3 HP/2 levels and raises the late-game cap, but it is weaker around normal acquisition levels and reduces temporary-HP duration from 1 hour to 5 turns. |
| Dire Charm | INCLUDE | SR doubles duration from vanilla 5 rounds to 1 turn without adding a corresponding mechanical drawback. Clear buff. |
| Ghost Armor | SKIP / MIXED | SR makes the spell castable on others and adds +20% Hide in Shadows, but worsens casting time (1 -> 3), shortens duration (1 hour -> 10 turns), changes school, and adds Detect Illusion interaction. |
| Minor Spell Deflection | SKIP / MIXED | SR increases capacity from 4 to 6 spell levels and uses a long fixed duration, but reduces the highest spell level it can absorb from 7th to 4th. |
| Protection from Fire | SKIP / TACTICS REMIX + MIXED | Tactics Remix Spell Tweaks extends Protection from Fire. SR also moves it from Level 3 to Level 4 while increasing protection from 50% to 100%. Do not disturb Tactics and do not import the level-shift tradeoff. |
| Protection from Cold | SKIP / MIXED | SR raises cold protection from 50% to 100% but moves the spell from Level 3 to Level 4 and increases casting time. Not a pure Level-3 buff. |
| Spell Thrust | SKIP / MIXED | Vanilla strips all protections of Level 5 or lower from one target. SR becomes a 15-ft. AoE but removes only one highest-level protection per target. Major tradeoff. |
| Detect Illusion | INCLUDE — ADAPTED | SR doubles radius (15 -> 30 ft.) and expands detection through 4th-level illusions, including Improved Invisibility. However, vanilla can also remove Non-Detection while SR's list omits it. Import the SR expansion while retaining vanilla Non-Detection removal, making this a strict buff. |
| Hold Undead / Halt Undead | SKIP / ZSTWEAKS | ZSTweaks component 502 makes Hold Undead bypass Magic Resistance and improves its save behavior. Preserve ZS. SR also trades duration scaling for a fixed turn and therefore is not independently a pure buff. |
| Melf's Minute Meteors | SKIP / TACTICS REMIX + MIXED | The target Tactics setup uses its dedicated MMM enchantment component. SR lowers enchantment to +2 and trades vanilla's higher average per-meteor damage for a wider damage range. Do not overwrite Tactics. |
| Dispel Magic | SKIP / TACTICS REMIX | Tactics Remix has a dedicated Remove/Dispel Magic cast-level component and scripts expect its spell-system behavior. Preserve Tactics. |
| Icelance | SKIP / IWDIFICATION + ZSTWEAKS | IWDification already supplies WIZARD_ICELANCE/SPWI327 and distributes its scroll. ZSTweaks component 452 further scales Icelance damage up to 10d6, which is substantially stronger than SR's fixed 5d6 implementation. |

## Final selected set

### ACCEPT REPLACEMENT
- Clairvoyance — full SR combat-oriented replacement of the vanilla map-reveal spell

### INCLUDE
- Dire Charm

### INCLUDE — ADAPTED
- Hold Person — SR save/radius improvement, vanilla casting time 3 retained
- Detect Illusion — SR radius/4th-level illusion expansion, while retaining vanilla ability to remove Non-Detection

Everything else is deliberately left to vanilla, Tactics Remix, ZSTweaks, or IWDification.

## Priority-mod notes

### Tactics Remix 8.2
Relevant Level-3 interactions:
- Skull Trap: Spell Tweaks component caps damage at 12d6
- Remove Magic / Dispel Magic: dedicated cast-level component
- Melf's Minute Meteors: dedicated enchantment-level component in the target Tactics setup
- Protection from Fire: Spell Tweaks extends duration

### ZSTweaks Arcane Magic group
The default/user-selected group includes the following Level-3 overlaps:
- 446 — Fireball improvements
- 452 — Icelance scaling
- 502 — Hold Undead bypasses Magic Resistance
- 577 — Haste / Improved Haste duration rebalance

The previously stated user exceptions for ZSTweaks are Magic Missile and Chromatic Orb; neither affects this Level-3 audit.

### IWDification
- WIZARD_ICELANCE / SPWI327 is already installed and distributed by IWDification.
- WIZARD_MONSTER_SUMMONING_1 / SPWI309 belongs to IWDification's coherent Monster Summoning I -> II -> III progression at Levels 3 -> 4 -> 5. SR's repurposing of SPWI309 as “Monster Summoning III” is therefore rejected.

## Scroll implications

No new Level-3 spell is added, so there is no additional new-scroll distribution task.

Clairvoyance is an in-place replacement and inherits the existing Clairvoyance scroll distribution.

Hold Person, Dire Charm, and Detect Illusion are in-place revisions and retain their existing scroll resources/distribution.

## Status

**CLOSED for spell selection and implemented in component #0.**

Further Level-3 changes should be limited to technical fixes found during install/in-game testing.
