# Crash points

## EverDrive / real hardware

Observed crashes while testing BGM changes:

1. Early Bowser / Star Spirits sequence
   - crash right before / during Star Spirits healing Mario
   - happens before entering Goomba Village

2. Goomba Village / house transition
   - another build survived until player control
   - crash happened after entering Goomba family house
   - Goomba Village BGM is already playing through the area before entering the house

3. Star Rod combined BGM replacement tests
   - single-song changes often appear okay
   - many combined changes crash during early scripted music transitions

## Emulator

Some full decomp BGM-change builds were able to run in emulator, but failed on EverDrive.
