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

## Scroll distribution roadmap

### Dimension Jump
The upstream SR implementation reuses an already distributed scroll resource. Before release, verify how those placements behave in EET and ensure the standalone Dimension Jump scroll inherits or reproduces appropriate distribution **without deleting another spell's scroll**.

### Obscuring Mist
Upstream SR replaces Blindness and can therefore reuse the Blindness scroll. This project keeps Blindness, so Obscuring Mist must retain a unique scroll resource.

Before release, dynamically inject the Obscuring Mist scroll into appropriate EET scroll distribution. Preferred behavior:
1. Keep every existing Blindness scroll untouched.
2. Detect stores that contain the Blindness scroll and add Obscuring Mist alongside it where appropriate.
3. Audit non-store placements (CRE/area/container or other scripted placements) and duplicate only suitable learnable-scroll placements rather than replacing them.
4. Avoid duplicate stock entries when reinstalling or when another component has already added the new scroll.

This distribution task is intentionally deferred until the arcane spell set is complete, so all new scrolls can be distributed coherently in one pass.
