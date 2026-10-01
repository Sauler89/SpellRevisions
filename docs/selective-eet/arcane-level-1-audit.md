# Arcane Level 1 Audit — Selective EET Spell Revisions

Target priority: Tactics Remix > ZSTweaks > IWDification > selected Spell Revisions changes.

| Spell | Decision | Reason |
|---|---|---|
| Grease | SKIP / ZSTWEAKS | ZSTweaks component 430 substantially rebuilds Grease (custom resources, repeated/scaling effects and description). Preserve ZS. |
| Armor / Mage Armor | INCLUDE | SR adds useful AC scaling (base AC improves from 6 to 3 by level 12). Clear long-term buff. Keep the classic BG-style description format. |
| Burning Hands | INCLUDE | SR trades slightly lower unsaved raw damage for no saving throw, longer reach and reliable scaling to 5d6. Overall offensive buff. Preserve the vanilla spell school to avoid unrelated specialist-mage changes. |
| Charm Person | INCLUDE | SR improves the save modifier from +3 to +2 for the target. Direct buff. |
| Color Spray | SKIP / MIXED-NERF | SR replaces the classic low-HD 5-round unconsciousness with slow/blind/confusion scaling. Better longevity, but materially weaker at low levels; not a pure buff. Tactics' old Color Spray code is commented out and is not the reason for the skip. |
| Blindness | KEEP TACTICS VERSION | Tactics Remix Spell Tweaks directly modifies Blindness. Do not replace it with SR Obscuring Mist. |
| Obscuring Mist | ADD AS NEW SPELL | Explicitly desired. Install as a separate level-1 arcane spell with its own resource/IDS entry and scroll handling; Blindness remains untouched. |
| Friends / Monster Summoning I | SKIP SR REPLACEMENT | Preserve Friends. IWDification already supplies Monster Summoning I (as its IWD spell at level 3); avoid a duplicate same-name spell. |
| Protection from Petrification | SKIP / NO MATERIAL BUFF | Current SR main component only updates name/description for this spell; no worthwhile mechanical buff to import. |
| Identify | SKIP / NO MATERIAL BUFF | No meaningful gameplay buff worth importing; preserve vanilla behavior and classic text. |
| True Strike / Infravision | ACCEPT REPLACEMENT | Explicitly desired. True Strike replaces Infravision; +4 THAC0 and +5% critical-hit chance for 3 rounds. |
| Magic Missile | SKIP / ZSTWEAKS | ZSTweaks component 572 heavily rebuilds Magic Missile and adds Invoker-specific behavior. Preserve ZS. |
| Protection from Evil | SKIP / MIXED | SR extends/normalizes protection and adds saving-throw benefits but changes the classic anti-evil/summoned-creature behavior. Not a pure buff. |
| Shield | SKIP / MIXED | SR changes fixed/base AC behavior into an additive AC bonus. This can be better for some characters and worse for others; not a pure buff. |
| Shocking Grasp | INCLUDE | SR persists through missed attacks, gives +4 to hit, scales to 5d6, can stun, and was explicitly changed to work against any creature / bypass PfMW. Clear buff. Preserve vanilla school to avoid unrelated specialist changes. |
| Sleep | SKIP / TACTICS REMIX | Tactics Remix Spell Tweaks directly modifies Sleep (including wake-on-hit behavior). Preserve Tactics. |
| Chill Touch | INCLUDE | SR makes the touch much more reliable (+4 to hit), gives +1 effective enchantment, guaranteed cold damage and a long Strength-drain rider unless saved. Net buff. |
| Chromatic Orb | SKIP / ZSTWEAKS | ZSTweaks component 555 completely rebuilds Chromatic Orb with custom projectiles/subspells and scaling. Preserve ZS. |
| Larloch's Minor Drain | SKIP / MIXED-NERF | SR scales from 2 to 10 drain, but it is weaker than vanilla at caster levels 1–2. Under the buff-only rule, skip it. |
| Reflected Image | INCLUDE | SR image no longer disappears simply from being struck and instead lasts until dispelled/detected/duration expiry. Despite different scaling duration, this is a substantial defensive buff. |
| Find Familiar | INCLUDE — SCHOOL ONLY | SR's familiar rebalance was reverted; the useful surviving change is making Find Familiar Universal. Apply only that change, leaving familiar resources/stats and classic description alone. |
| Nahal's Reckless Dweomer | SKIP | SR mainly changes classification/technical presentation here; no clear standalone buff under the selective rules. |
| Spook | SKIP / MIXED-NERF | Duration rises from 3 to 5 rounds, but maximum save penalty is reduced from -6 to -4 and extra immunities are added. Not a pure buff. |
| Expeditious Retreat | INCLUDE / OVERRIDE IWDIFICATION | IWDification already adds it, but SR is substantially stronger: affects friendly creatures in the area and provides much greater movement. Detect and patch/replace the existing IWDification spell instead of adding a duplicate. |
| Dimension Jump | ADD AS NEW SPELL | New SR level-1 Conjuration spell; no overlap found in Tactics Remix, ZSTweaks, or IWDification. |
| Detect / Know Alignment | INCLUDE — ADAPTED | SR moves Detect Alignment to level 1 because it later repurposes the level-2 slot. For the selective mod, keep the existing Know Alignment resource/scroll and simply move the spell itself to level 1; do not create a duplicate and do not require the later Know Opponent replacement. |

## Level-1 selected set

Full SR mechanics to import selectively:
- Mage Armor
- Burning Hands
- Charm Person
- Shocking Grasp
- Chill Touch
- Reflected Image

Explicit replacements/additions:
- True Strike (replace Infravision)
- Obscuring Mist (new spell; Blindness retained)
- Dimension Jump (new spell)
- Expeditious Retreat (SR implementation supersedes IWDification's copy)

Small adapted buffs:
- Find Familiar: Universal school only
- Detect/Know Alignment: move existing spell to level 1 only

Everything else at arcane level 1 is deliberately left to vanilla/Tactics Remix/ZSTweaks/IWDification.

## Implementation constraints

- Do not overwrite Tactics Remix's Sleep or Blindness.
- Do not overwrite ZSTweaks' Grease, Chromatic Orb, or Magic Missile.
- Do not replace Friends.
- Obscuring Mist must use a new unique resource and must not occupy SPWI106.
- When IWDification is installed, Expeditious Retreat must reuse/patch its registered WIZARD_EXPEDITIOUS_RETREAT resource rather than creating a duplicate.
- Existing spells retain classic BG/EE description formatting. New spells receive descriptions written in that same classic format rather than Spell Revisions' modern formatted style.
- Avoid importing unrelated SR school changes when the selected buff does not require them.
