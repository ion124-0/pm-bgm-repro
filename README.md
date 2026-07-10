# Paper Mario BGM change crash repro

This is a small repro to get help with crashes that occur on Everdrive when trying to change the bgm of Paper Mario on N64.

## Goal

Fix hardware crashes.

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
  - did not produce a reliable working test ROM; emulator testing was not a valid success case

### Star Rod / BGM replacement route

Injecting just one modded bgm file at a time doesn’t crash, so there’s no way to isolate any individual bgm file as the cause. The crash happens if you have a bunch of modded bgm files, individual modded files don’t cause it to crash, but multiple ones cause it to break resume/pop/fade behavior. 

Crash points observed include:

- majority of crashes occured when Mario and Luigi first reached Peach's Castle Party
- both before and during Star Spirits healing Mario after the first Bowser fight
- after taking control near Goomba Village
- entering the Goomba family house / Goomba Village transition

## Included here

- source diffs for BGM-control experiments
- small scripts used for BGM mapping/diff analysis
- text reports and crash notes
- ROM size/hash notes
