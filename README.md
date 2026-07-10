# Paper Mario bgm change crash repro

This is a small repro to get help with crashes that occur on EverDrive when trying to change Paper Mario 64 bgm behavior or bgm assets.

## Goal

Fix hardware crashes caused by bgm changes.

## Observed issues

### Decomp route

A clean decomp build produced a valid vanilla ROM:

- `papermario_vanilla_decomp_clean2.z64`
- size: `41943040`
- CRC good

Problem builds observed:

A clean vanilla DX build worked on Mupen emulator but not on Everdrive and not even on Project64. DX build crashes on Everdrive and PJ64, even when vanilla.

This build here was one of many tests made in the Decomp that involved placing changed bgm files that were made in mamar into assets/mod/audio, and having them replace the original bgm files that were in assets/us/audio. The rom made, but crashes on both emulator and original hardware.
- `papermario_nm_global_volume_zero_test.z64`
  - size: `41943024`
  - 16 bytes shorter than clean decomp base

Other attempts included:
**Changing `bgm_control.c`. **
Those builds crashed on boot on EverDrive with a TLB exception error. 
**Rebuilding and injecting a new `audio.sbn` into a working ROM and direct hex edits. **
These produced the same types of crashes. 

Every single modded rom with multiple bgm changes has crashed, regardless of whether it was made in Paper Mario Decomp or Star Rod Classic v0.5.3, DX builds never work in EverDrive.

### Star Rod / bgm replacement route

Injecting one custom/modded bgm file from Mamar does not appear to crash by itself during the tested resume/pop/fade paths, including `snd_song_request_pop`, `bgm_update_music_control`, and `au_bgm_process_resume`.

Roms with single bgm file changes don't crash. Crashes occur when multiple bgm files are changed together, which means it's not any one bad modded bgm file that's causing the issue.

Crash points observed include:

- During the first dialogue box after Mario and Luigi first enter Peach's Castle party
- before or during Star Spirits healing Mario after the first Bowser fight
- after taking control near Goomba Village and entering the Goomba house

## Included here

- source diffs for bgm-control experiments
- text reports and crash notes
- ROM size/hash notes

No ROMs or extracted assets are included.
