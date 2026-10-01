# Selective Spell Revisions for EET

A personal, compatibility-oriented spell overhaul for **Enhanced Edition Trilogy (EET)**, built from **Spell Revisions v4.21** as a source base while deliberately selecting only the changes wanted for this installation.

This is **not** the original Spell Revisions installer. The project has its own main WeiDU component and is designed around a load order where **Tactics Remix**, **IWDification**, and selected **ZSTweaks** components take priority.

## Design goals

- Preserve Tactics Remix spell behavior whenever its Spell Tweaks component substantially changes the same spell.
- Preserve selected ZSTweaks spell overhauls where they are actually used.
- Avoid duplicate IWDification spells.
- Allow a Spell Revisions implementation to supersede IWDification when it is a deliberately selected improvement.
- Import only Spell Revisions changes judged to be buffs, useful fixes, desirable replacements, or worthwhile additions.
- Skip pure nerfs and mixed rebalance changes unless explicitly approved.
- Keep classic Baldur's Gate / Enhanced Edition-style English spell descriptions instead of the reformatted Spell Revisions presentation.
- Treat every spell replacement explicitly rather than inheriting all of Spell Revisions wholesale.

## Main component

WeiDU component:

- **#0 — Selective Spell Revisions for EET**

The installer exposes this project as the main component. The original Spell Revisions main component is no longer part of this branch's installer.

Completed spell modules are aggregated by:

`spell_rev/components/selective_eet_main.tpa`

Completed modules currently included in component #0:

- Arcane Level 1
- Arcane Level 2
- Arcane Level 3
- Arcane Level 4

Further arcane and divine levels will be added to the same component as their audits are completed.

## Arcane Level 1

Included Spell Revisions mechanics:

- Mage Armor
- Burning Hands
- Shocking Grasp
- Chill Touch
- Reflected Image

Accepted replacements / additions:

- True Strike replaces Infravision
- Obscuring Mist is added as a new spell; Blindness remains intact
- Dimension Jump is added as a new spell
- Expeditious Retreat uses the selected SR implementation and supersedes IWDification's copy when present

Adapted change:

- Find Familiar: only the Universal-school change is imported

The detailed spell-by-spell audit is in:

`docs/selective-eet/arcane-level-1-audit.md`

## Arcane Level 2

Included buffs:

- Strength
- Ghoul Touch (SR mechanics with vanilla casting time retained)
- Power Word Sleep (SR mechanics with vanilla Conjuration/Summoning school retained)

Accepted replacements:

- Detect Alignment completely replaces Know Alignment and moves to Level 1
- Battering Ram completely replaces Knock
- Sound Burst completely replaces Deafness

New spell:

- Resist Elements

Know Opponent is intentionally not imported.

The detailed spell-by-spell audit is in:

`docs/selective-eet/arcane-level-2-audit.md`

## Arcane Level 3

Accepted replacement:

- Clairvoyance uses the full SR combat-oriented replacement of the vanilla map-reveal spell

Included buff:

- Dire Charm

Adapted buffs:

- Hold Person: SR save/AoE improvement with vanilla casting time 3 retained
- Detect Illusion: SR radius/4th-level illusion expansion while retaining vanilla removal of Non-Detection

The detailed spell-by-spell audit is in:

`docs/selective-eet/arcane-level-3-audit.md`

## Arcane Level 4

Adapted buffs:

- Confusion: SR 30-ft. area with vanilla scaling duration retained
- Break Enchantment completely replaces Remove Curse, with vanilla casting time 4 retained and the ZSTweaks Rashad's Talon hook preserved when present
- Secret Word keeps the installed Abjuration/protection-removal behavior while receiving SR's casting time 1 and longer range

Included buff:

- Farsight: SR 5-turn duration

New spell:

- Protection from Elemental Energy: dynamically allocated Level-4 spell with four hidden SR-derived subspells for 100% Acid, Cold, Fire, or Lightning protection

The detailed spell-by-spell audit is in:

`docs/selective-eet/arcane-level-4-audit.md`

## Scroll distribution policy

New spell scrolls must not silently remove vanilla or higher-priority-mod scrolls.

### Dimension Jump

Spell Revisions normally reuses the existing Dimension Door scroll resource, which naturally inherits its existing placements. Because this project preserves other spells rather than blindly replacing their resources, final integration must verify the original SR distribution behavior and ensure **Dimension Jump receives proper EET scroll distribution without destroying an existing scroll**.

### Obscuring Mist

Spell Revisions normally replaces Blindness and therefore reuses Blindness's scroll distribution. This project keeps Blindness, so Obscuring Mist uses its own scroll resource.

Before release, the installer must **dynamically distribute the new Obscuring Mist scroll** through the EET installation. The preferred approach is to identify relevant existing level-1 arcane scroll placements (especially Blindness placements) and add the new Obscuring Mist scroll alongside them rather than replacing the original item.

Distribution must account for stores and, where relevant, other EET resources that can carry learnable scrolls.

### Protection from Elemental Energy

Protection from Elemental Energy uses its own scroll resource, `DVPEESCR.ITM`, and must be added dynamically during the final EET arcane-scroll distribution pass. Its hidden protection subspells are internal implementation resources and are not learnable spells.


See `SELECTIVE_EET_DESIGN.md` for the full compatibility rules.

## Credits and source base

This project is derived from and reuses code/assets from **Spell Revisions** by its original authors and maintainers at Gibberlings3.

Upstream project:
https://github.com/Gibberlings3/SpellRevisions

Spell Revisions documentation:
https://gibberlings3.github.io/SpellRevisions/

The upstream documentation may lag behind the current v4.21 source; when documentation and source differ, this project audits the actual source used by the installer.

## Status

**Early development / alpha.**

The current branch is intended for development and controlled testing on EET, not yet as a finished general-purpose release.
