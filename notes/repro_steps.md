# Repro steps

This repo does not include ROMs, baseroms, built ROMs, or extracted assets.

Expected setup:
1. Use a clean Paper Mario decomp checkout.
2. Build a clean vanilla ROM with the user's own legal baserom.
3. Confirm clean vanilla output size is 41943040 bytes.
4. Apply the included `bgm_control` patch/diff manually or with patch tooling.
5. Rebuild.
6. Compare output ROM size against the clean vanilla output.
7. Test in emulator and on EverDrive / real hardware.

Observed result:
- Clean vanilla decomp build: 41943040 bytes, CRC good.
- BGM-control modified builds changed ROM size by +/- 16 bytes in prior tests.
- Some BGM-change builds ran in emulator but failed on EverDrive.
- Star Rod / BGM replacement route produced tiny single-song diffs, but combined changes crashed during early scripted BGM transitions.
