# Selective Spell Revisions for EET

This is an autonomous EET spell-overhaul mod derived from Spell Revisions v4.21. Spell Revisions is the source base, but the installer, component structure, selection policy, and final spell set belong to this project.

The mod is intended for an EET installation where **Tactics Remix**, **IWDification**, and selected **ZSTweaks** components take priority over Spell Revisions.

## Selection rules

1. **Tactics Remix and ZSTweaks have priority.**
   - If their spell-tweak components substantially alter a spell also changed by Spell Revisions, the Spell Revisions version is excluded.
   - The goal is to preserve the spell behavior expected by Tactics Remix AI and by ZSTweaks.

2. **IWDification overlap is evaluated spell by spell.**
   - If Spell Revisions merely duplicates a spell already supplied by IWDification, the Spell Revisions copy is excluded.
   - If Spell Revisions provides a clearly stronger/better implementation that is intentionally desired, the SR implementation may replace the IWDification version.

3. **Only beneficial SR revisions are candidates.**
   - Buffs, useful fixes, desirable replacements, and selected new spells are candidates.
   - Pure nerfs are excluded unless they are technically required by an included spell.

4. **Descriptions keep the classic BG/EE presentation style.**
   - Included revisions should not use the reformatted Spell Revisions description style.
   - Existing vanilla descriptions should be preserved where practical; new/replacement spells should follow the classic in-game English formatting.

5. **Replacement policy is explicit.**
   - Some SR replacements are accepted (example: True Strike replacing Infravision).
   - Some replacements are converted into additions (example: Obscuring Mist should be retained without replacing/removing Blindness).
   - No replacement is accepted implicitly.

## Compatibility audit categories

Each affected spell will be classified as one of:

- INCLUDE — SR change is beneficial and does not conflict with higher-priority mods.
- INCLUDE / OVERRIDE IWDIFICATION — desired SR implementation intentionally supersedes IWDification.
- ADD AS NEW SPELL — retain SR content without replacing a vanilla spell.
- ACCEPT REPLACEMENT — SR replacement is explicitly desired.
- SKIP / TACTICS REMIX — preserve Tactics Remix behavior.
- SKIP / ZSTWEAKS — preserve ZSTweaks behavior.
- SKIP / DUPLICATE IWDIFICATION — avoid duplicate spell.
- SKIP / NERF — SR change is primarily a nerf.
- REVIEW — interaction is ambiguous or depends on installer options.

## Initial explicit decisions

- **Obscuring Mist:** include, but as an additional spell; do not sacrifice Blindness.
- **True Strike:** include; replacing Infravision is acceptable.

The final installer should be built from an explicit allowlist rather than installing the full Spell Revisions main component and trying to undo unwanted changes afterward.


## Installer architecture

- Component **#0** is the project's single main component: `Selective Spell Revisions for EET`.
- The original Spell Revisions main component is not exposed by this project's installer.
- Completed spell-level modules are included from `spell_rev/components/selective_eet_main.tpa`.
- New levels are added to that main aggregator after their audit is closed.

## Current arcane scroll distribution

All genuinely new arcane scrolls are currently distributed through **Lucy the Wyvern** in the Adventure Mart, using the **Shards of Ice** store resource `U!LSTORE.STO`.

The installer appends five identified copies of each scroll and does not remove or replace Lucy's existing stock:

- `DVOBMSCR.ITM` — Obscuring Mist
- `DVDJMSCR.ITM` — Dimension Jump
- `DVRESSCR.ITM` — Resist Elements
- `DVPEESCR.ITM` — Protection from Elemental Energy
- `DVMASSCR.ITM` — Mestil's Acid Sheath
- `DVBANSCR.ITM` — Banishment
- `DVDKSCR.ITM` — Summon Death Knight
- `DVGHSCR.ITM` — Ghostform

The patch is conditional on `U!LSTORE.STO` existing, so installations without the relevant Shards of Ice Lucy shop do not fail. This is the current centralized development/test distribution and supersedes the earlier deferred unified-scroll roadmap. Permanent world/store distribution can be revisited later.

### Level-2 replacements and scroll inheritance
- Detect Alignment replaces Know Alignment and converts existing learnable Know Alignment scrolls to the new Level-1 resource.
- Battering Ram replaces Knock in-place and therefore inherits Knock's scroll distribution.
- Sound Burst replaces Deafness in-place and therefore inherits Deafness's scroll distribution.


### Level-3 decisions
- Clairvoyance: accept the full SR replacement. The vanilla map-reveal function is intentionally removed in favor of SR's defensive combat divination.
- Hold Person: import SR's stronger save penalty and larger splash radius, but retain vanilla casting time 3.
- Dire Charm: import the SR duration buff.
- Detect Illusion: import SR's larger radius and 4th-level illusion removal, while explicitly preserving vanilla removal of Non-Detection through resource-based dispelling.
- No new Level-3 scroll distribution is required because all selected Level-3 changes are in-place replacements/revisions.


### Level-4 decisions
- Confusion: retain vanilla range and scaling duration, but expand the area to SR's 30-ft. radius.
- Break Enchantment: completely replaces Remove Curse. Use SR mechanics, retain vanilla casting time 4, and preserve the ZSTweaks Rashad's Talon hook when the corresponding resource is present.
- Secret Word: retain the installed Abjuration school and existing Level-8-or-lower protection-removal behavior; import only SR's casting time 1 and longer range.
- Farsight: use the SR 5-turn duration.
- Protection from Elemental Energy: add as a new dynamically allocated Level-4 spell. Do not reuse IWDification's SPWI426. The selection menu points to four hidden SR-derived subspells (DVPEEFIR, DVPEECOL, DVPEEELE, DVPEEACI) so the spell always provides 100% protection without replacing the retained elemental-protection spells.
- Protection from Elemental Energy scroll: `DVPEESCR.ITM`; currently stocked at Lucy's `U!LSTORE.STO` (5 copies).


### Level-5 decisions
- Domination: preserve the installed spell and extend its charm duration from 8 rounds to 1 turn.
- Hold Monster: preserve vanilla 1 round/level duration and -2 save penalty, but use SR's 5-ft. splash area.
- Feeblemind: preserve the installed spell and strengthen its Save vs. Spell penalty from -2 to -4.
- Lower Resistance: use SR's scalable implementation, but preserve the vanilla Abjuration school and 40-ft. range. Use 19% at caster level 9, then 2%/level from level 10 onward, capped at 40%.
- Oracle: preserve vanilla 120-ft. radius and Non-Detection removal; add SR coverage for Blur, Ghost Armor, Invisibility Sphere, Pixie Dust, Mislead, Project Image, and Mass Invisibility.
- Mestil's Acid Sheath: add as a new dynamically allocated Level-5 spell. Never reuse IWDification's SPWI526 (Summon Shadow). Its retaliation subspell is renamed to `DVMASDMG.SPL`.
- Mestil's Acid Sheath scroll: `DVMASSCR.ITM`; currently stocked at Lucy's `U!LSTORE.STO` (5 copies).


### Level-6 decisions
- Globe of Invulnerability: preserve installed protection semantics; raise any positive duration shorter than 2 turns to 2 turns, while retaining longer vanilla high-level scaling.
- Power Word, Silence: preserve installed mechanics and vanilla Conjuration/Summoning school; extend the vanilla 7-round duration to 1 turn.
- Contingency: change only to Universal school, clearing specialist exclusions on both the spell and its scroll.
- Banishment: add as a new dynamically allocated Level-6 Abjuration. Never overwrite Death Spell/SPWI605; Death Spell remains fully available for Tactics semantics.
- Banishment scroll: `DVBANSCR.ITM`; currently stocked at Lucy's `U!LSTORE.STO` (5 copies).
- Flesh to Stone: keep installed/vanilla version. SR's implementation is a mixed redesign tied to its global petrification framework rather than a clean buff.
- Stone to Flesh: keep installed/vanilla version. Full SR hides/disables the player spell rather than improving it.


### Level-7 decisions
- Protection from the Elements: use the full SR upgrade (100% elemental resistance; 1 turn per 2 levels).
- Ruby Ray of Reversal: preserve the installed/Tactics removal list and import only SR's 30-ft. range.
- Spell Sequencer: change only to Universal school and clear specialist exclusions.
- Delayed Blast Fireball: preserve ZSTweaks #446 completely. That component directly rebuilds SPWI712, so the selective module must not patch SPWI712 or SCRL8N.
- Power Word, Stun: use SR's additional 1-round stun for targets with 90+ HP, but preserve vanilla Conjuration/Summoning school.
- Summon Djinni: preserve installed summon assets and add only 8 rounds to the summon duration.
- Mass Invisibility: preserve all installed/ZSTweaks effects and import only SR's 30-ft. area projectile.
- Limited Wish: change only to Universal school and clear specialist exclusions.
- Summon Death Knight: add as a new dynamically allocated Level-7 spell. Preserve Cacofiend completely. Copy SR's SPCACO.EFF as `DVDKTEFF.EFF` and retarget only the new spell; use `DVDKSCR.ITM` as its dedicated scroll, currently stocked at Lucy's `U!LSTORE.STO` (5 copies).
- Prismatic Mantle: not selected because Tactics owns the physical-defense hierarchy.


### Level-8 decisions
- Ghostform: add as a new dynamically allocated Level-8 Alteration. IWDification owns SPWI801, so never overwrite it. Retarget Ghostform's internal SPWI801 self-immunity reference to the final dynamic resource; use `DVGHSCR.ITM` as its dedicated scroll, currently stocked at Lucy's `U!LSTORE.STO` (5 copies).
- Protection from Energy: use the full SR upgrade (100% acid/cold/electricity/fire/magic damage protection; 2 rounds/level).
- Spell Trigger: change only to Universal school and clear specialist exclusions.
- Incendiary Cloud: preserve installed/vanilla Evocation school, 1d4/level damage and Save vs. Spell; import SR's 30-ft. cloud projectile and no-save -4 THAC0/-4 AC smoke penalties.
- Power Word, Blind: preserve installed AoE/projectile and Conjuration/Summoning school; extend normal blindness from 6 rounds to 1 turn and mirror SR's permanent blindness for targets below 6 HD.
- Symbol, Stun: preserve installed scaling duration, -4 save and casting time; import SR's 20-ft. symbol projectile.
- Symbol, Death: preserve installed casting time and 60-current-HP limit; import SR's 20-ft. symbol projectile and -4 Save vs. Death penalty.
- Mind Blank: preserve IWDification.
- Pierce Shield and Improved Mantle: preserve Tactics.
- Abi-Dalzim's Horrid Wilting, Maze and Bigby's Clenched Fist: preserve ZSTweaks.
- Moment of Prescience, Symbol of Weakness and Bigby's Icy Grasp: explicitly not added.


### Level-9 decisions
- Chain Contingency: change only to Universal school and clear specialist exclusions on spell and scroll. Preserve installed mechanics and casting time 9.
- Freedom: use SR's expanded mass-freedom/cure implementation while retaining vanilla Maze/Imprisonment release. Restore casting time 9 instead of SR's 1 round.
- Spell Trap, Spellstrike, Gate and Absolute Immunity: preserve Tactics semantics.
- Imprisonment, Meteor Swarm, Power Word Kill, Wail of the Banshee, Energy Drain, Black Blade of Disaster and Bigby's Crushing Hand: preserve ZSTweaks.
- Shapechange and Time Stop: keep installed/vanilla versions.
- Wish: keep existing implementation and all Tactics/ZSTweaks subspell hooks.
- SR Monster Summoning IX: not used; source block is disabled and IWDification already owns WIZARD_MONSTER_SUMMONING_7.
