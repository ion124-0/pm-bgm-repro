# Paper Mario BGM change crash repro

This is a small reproduction package for crashes encountered while changing Paper Mario 64 BGM behavior / BGM assets.

This repo intentionally does not include:
- ROMs
- baseroms
- built game files
- extracted game assets
- BGM files
- Nintendo assets

## Goal

Investigate why BGM changes that appear to build or run in emulator can crash on real hardware / EverDrive, and why combined BGM replacement changes crash during early scripted music transitions.

## Observed issues

### Decomp route

A clean decomp build produced a valid vanilla ROM:

- `papermario_vanilla_decomp_clean2.z64`
- size: `41943040`
- CRC good

Problem builds observed:

- `papermario_nm_global_volume_zero_test.z64`
  - size: `41943024`
  - 16 bytes shorter than clean decomp base
  - ran in emulator in earlier testing, but failed on EverDrive

- `papermario_nm_song_request_volume_1_test.z64`
  - size: `41943056`
  - 16 bytes larger than clean decomp base

Because these no longer match the clean base size, they are not safe for direct byte-patch comparison.

### Star Rod / BGM replacement route

Single BGM changes often produce tiny ROM diffs and do not always crash by themselves.

Combined BGM changes crash during early music transitions. Crash points observed include:

- before / during Star Spirits healing Mario after the first Bowser scene
- after taking control near Goomba Village
- entering the Goomba family house / Goomba Village transition

This suggests the issue may involve BGM transition/resume/fade/push/pop behavior rather than one obviously bad BGM file.

## Included here

- source diffs for BGM-control experiments
- small scripts used for BGM mapping/diff analysis
- text reports and crash notes
- ROM size/hash notes

No ROMs or extracted assets are included.
