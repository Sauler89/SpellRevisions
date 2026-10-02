# Arcane Levels 1–9 — Technical Audit

Scope: component #0 (`Selective Spell Revisions for EET`), Arcane Levels 1–9 plus the temporary Lucy scroll distribution.

This audit is a strict static/source QA pass. It checks WeiDU structure, custom helpers, source assets, dynamic spell resources, private resrefs, selected SR dependencies, string references, scroll resources, store distribution, and documentation consistency.

## Result

**STATIC QA: PASS WITH FIXES APPLIED**

No unresolved source-level blocker was found after the corrections below.

A real WeiDU install/compile against the target EET installation is still required before the branch can be considered install-tested.

## Fixes applied during this audit

### 1. Missing selective helper functions — FIXED

Levels 5–7 called the following `DVSEL_*` helpers but they were not defined anywhere in the autonomous installer:

- `DVSEL_SET_EFFECT_DURATION_RANGE`
- `DVSEL_ADD_EFFECT_DURATION`
- `DVSEL_SET_SAVE_BONUS_ON_SAVING_EFFECTS`

These are now defined once in `selective_eet_arcane_level_1.tpa`, which is the first module included by component #0.

They use direct SPL/ITM V1 effect-table iteration and therefore do not depend on full Spell Revisions' main component.

### 2. Summon Death Knight missing teleport dependency — FIXED

`DVDEATHK.BCS` uses Spell Revisions' custom `DVTELPOR.SPL` (Teleport Without Error).

Full Spell Revisions copies that resource globally, but the selective component did not.

The dependency is now isolated:

- SR `DVTELPOR.SPL` -> private `DVDKTELP.SPL`
- `DVDEATHK.BCS` is retargeted from `dvtelpor` to `dvdktelp`

This keeps the Death Knight self-contained without importing an unnecessary global SR resource.

### 3. Delayed Blast Fireball priority documentation — FIXED

ZSTweaks component #446 directly rebuilds `SPWI712` Delayed Blast Fireball, in addition to its Fireball/Sunfire work.

The Level-7 implementation already correctly preserved ZSTweaks and did not patch `SPWI712` or `SCRL8N`, but older README/design/audit text still described the discarded SR hybrid.

README, design notes and Level-7 audit are now aligned with the actual priority rule:

**ZSTweaks #446 owns Delayed Blast Fireball.**

## Structural checks

### Component ordering

`selective_eet_main.tpa` includes:

1. Arcane Level 1
2. Arcane Level 2
3. Arcane Level 3
4. Arcane Level 4
5. Arcane Level 5
6. Arcane Level 6
7. Arcane Level 7
8. Arcane Level 8
9. Arcane Level 9
10. Arcane scroll distribution

This guarantees helper definitions and newly generated scroll resources exist before the Lucy store patch executes.

### Source-file existence

Every literal `spell_rev/...` source path referenced by the Arcane Level 1–9 modules was checked against the current branch tree.

**Missing source assets: 0**

### Translation references

All `@30xxx` references used by the Arcane Level 1–9 modules were checked against:

`spell_rev/languages/english/selective_eet.tra`

Results:

- missing referenced strings: **0**
- duplicate string IDs: **0**

### Private resource lengths

All private/generated literal resrefs checked are within the Infinity Engine 8-character resource-name limit.

Examples include:

- `DVOBMI01`
- `DVPEELEM`
- `DVMASDMG`
- `DVDKTEFF`
- `DVDKTELP`
- `DVBANSCR`

No overlength literal resource name was found.

## Dynamic spell audit

### Obscuring Mist

- Blindness remains untouched.
- New spell is added through `ADD_SPELL`.
- Internal `SPWI106I` reference is redirected to private `DVOBMI01.EFF`.
- The private EFF's resource reference is updated to the final dynamically assigned spell resource.
- Dedicated scroll: `DVOBMSCR.ITM`.

### Dimension Jump

- Added/reused dynamically as `WIZARD_DIMENSION_JUMP`.
- Does not overwrite an existing spell slot.
- Dedicated scroll: `DVDJMSCR.ITM`.

### Resist Elements

- Added/reused dynamically as `WIZARD_RESIST_ELEMENTS`.
- Internal `SPWI225` self references are retargeted to the actual assigned resource.
- Dedicated scroll: `DVRESSCR.ITM`.

### Protection from Elemental Energy

- IWDification's `SPWI426` remains untouched.
- Dynamic spell uses a private selection table `DVPEELEM.2DA`.
- Menu entries point to private protection subspells:
  - `DVPEEFIR`
  - `DVPEECOL`
  - `DVPEEELE`
  - `DVPEEACI`
- Dedicated scroll: `DVPEESCR.ITM`.

### Mestil's Acid Sheath

- IWDification's `SPWI526` remains untouched.
- Retaliation spell is private `DVMASDMG.SPL`.
- Internal `DVWI526D` and `SPWI526` references are retargeted.
- Source SPL binary casting time is 4, matching the selective description.
- Dedicated scroll: `DVMASSCR.ITM`.

### Banishment

- Death Spell `SPWI605` and `SCRL7I` remain untouched.
- Banishment is dynamically allocated.
- Required SR `DVBANISH.EFF/SPL` resources are explicitly copied.
- Dedicated scroll: `DVBANSCR.ITM`.

### Summon Death Knight

- Cacofiend `SPWI707`, `SPCACO.EFF`, and `SCRL8I` remain untouched.
- Private resources isolate SR dependencies:
  - `DVDKTEFF.EFF`
  - `DVDKUND.ITM`
  - `DVDKFEAR.SPL`
  - `DVDKFIRE.SPL`
  - `DVDKFIRI.EFF`
  - `DVDKSYMD.SPL`
  - `DVDKSYMW.SPL`
  - `DVDKTELP.SPL`
- Death Knight CRE/item/script references are retargeted where required.
- Dedicated scroll: `DVDKSCR.ITM`.

### Ghostform

- IWDification's `SPWI801` Monster Summoning VI remains untouched.
- Ghostform is dynamically allocated.
- All Ghostform self-references to source slot `SPWI801` are retargeted to the final dynamic spell resource.
- Dedicated scroll: `DVGHSCR.ITM`.

## Higher-priority compatibility checks

### ZSTweaks

The selective modules preserve known higher-priority resources where required, including:

- Delayed Blast Fireball — #446
- Finger of Death
- Control Undead
- Maze
- Horrid Wilting
- Bigby's Clenched/Crushing Hand
- Wail of the Banshee
- Meteor Swarm
- Energy Drain
- Imprisonment
- Power Word Kill
- Tenser's Transformation
- Chain Lightning
- Disintegrate
- Improved Haste
- Acid Fog

Symbol Death also includes a compatibility guard for the ZSTweaks Symbol-spell rewrite if its marker resource is present.

### Tactics Remix

The selective set does not overwrite the major Tactics-owned mage-chess / physical-defense resources identified during the spell audits, including:

- Spell Turning
- Khelben's Warding Whip
- Mantle
- Spell Trap
- Spellstrike
- Absolute Immunity
- Death Spell
- Protection from Magical Weapons

### IWDification

Known occupied/additional spell slots are preserved, including:

- `SPWI426`
- `SPWI526`
- `SPWI801`
- IWD Monster Summoning progression
- IWD Mind Blank

## Lucy scroll distribution audit

Store resource:

`U!LSTORE.STO`

The patch is conditional on the store existing.

Five identified copies are added for each genuinely new scroll:

- `DVOBMSCR` — Obscuring Mist
- `DVDJMSCR` — Dimension Jump
- `DVRESSCR` — Resist Elements
- `DVPEESCR` — Protection from Elemental Energy
- `DVMASSCR` — Mestil's Acid Sheath
- `DVBANSCR` — Banishment
- `DVDKSCR` — Summon Death Knight
- `DVGHSCR` — Ghostform

Existing Lucy stock is not removed or replaced.

If `U!LSTORE.STO` is absent, installation continues and emits a warning.

## Remaining test requirement

This audit does **not** claim a successful real WeiDU installation.

The final required validation is:

1. run the component against the user's real EET modded installation, after the intended higher-priority mods;
2. inspect `SETUP-SPELL_REV.DEBUG`;
3. verify all eight new scrolls in Lucy's shop;
4. learn/cast each new spell;
5. test the selected in-place spell modifications;
6. confirm Tactics/ZSTweaks/IWDification-owned spells retain their expected behavior.

Only after that run should the Arcane 1–9 block be considered fully install-tested.
