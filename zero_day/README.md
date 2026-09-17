# Zero-Day

Conversion script and scene information for Beeple's "Zero-Day" corridor from
NVIDIA ORCA, used by Bevy's `zero_day` example.

## Converted assets

The three converted glTF binaries (about 1.5 GB total) are distributed as GitHub
release assets:

- `zero_day_measure_one.glb`
- `zero_day_measure_seven.glb`
- `zero_day_measure_seven_colored_lights.glb`

They are available from the
[`zero-day-1.0` release](https://github.com/bevyengine/bevy_asset_files/releases/tag/zero-day-1.0).

## Converting from source

Alternatively, download and extract the FBX scene from
[NVIDIA ORCA](https://developer.nvidia.com/orca/beeple-zero-day) and convert it yourself.
Bevy can't read FBX files, so the `convert.py` script converts each measure into a glTF
binary with Blender 4 or Blender 5.

Run the following commands from this repository's root, replacing `/path/to/ZeroDay`
with the extracted scene directory containing `MEASURE_ONE` and `MEASURE_SEVEN`.
Keep each measure's `tex/` directory alongside its FBX files so the converter can
find the textures.

```console
blender --background --python-exit-code 1 --python zero_day/convert.py -- \
  "/path/to/ZeroDay/MEASURE_ONE/MEASURE_ONE.fbx" \
  "zero_day/zero_day_measure_one.glb"

blender --background --python-exit-code 1 --python zero_day/convert.py -- \
  "/path/to/ZeroDay/MEASURE_SEVEN/MEASURE_SEVEN.fbx" \
  "zero_day/zero_day_measure_seven.glb"

blender --background --python-exit-code 1 --python zero_day/convert.py -- \
  "/path/to/ZeroDay/MEASURE_SEVEN/MEASURE_SEVEN_COLORED_LIGHTS.fbx" \
  "zero_day/zero_day_measure_seven_colored_lights.glb"
```

## Scene license

"Zero-Day" is by Mike Winkelmann (Beeple), distributed through
[NVIDIA ORCA](https://developer.nvidia.com/orca/beeple-zero-day) under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The `.glb` files in the
release are modified from the original: converted from FBX to glTF, materials rebuilt,
hidden meshes removed, and animations baked. The converter also embeds attribution
in each `.glb` file's `asset.copyright` field.

The conversion script is dual-licensed under [MIT](LICENSE-MIT) or
[Apache-2.0](LICENSE-APACHE).
