# ROM sizes observed

Clean decomp vanilla builds:

- `papermario_vanilla_decomp_clean2.z64`: 41943040
- `base_clean3.z64`: 41943040
- CRC good on clean build

Problem decomp BGM-change builds:

- `papermario_nm_global_volume_zero_test.z64`: 41943024
  - 16 bytes shorter than clean base

- `papermario_nm_song_request_volume_1_test.z64`: 41943056
  - 16 bytes larger than clean base

Star Rod baseline / Star Rod output layout:

- Star Rod baseline all-vanilla-audio ROM: 41975920
- This is not the same layout as the clean decomp 41943040-byte ROM.
- Star Rod byte offsets should not be applied blindly to clean decomp baserom layout.

Patchertool64+ output:

- Same size as clean decomp in one test, but differed by thousands of bytes from clean decomp base.
- Not treated as clean base.
