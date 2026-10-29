# Licence notice: SetFlowBody.usdz and SetFlowAnatomy.usdz

The model combines two sources:
- the muscles, tendons and neutral parts, from Z-Anatomy and BodyParts3D under CC BY-SA 4.0 (below);
- since skin v4 (2026-10-28), the visible body: the `skin_*` region nodes, a human body surface from MakeHuman under CC0 1.0 (see "Skin v3 source" and "Skin v4" at the end).

## Credit (required)

This 3D model is derived from:

- **"Z-Anatomy - The libre 3D atlas of anatomy - CC-BY-SA 4.0"**
  Source: https://github.com/Z-Anatomy/Models-of-human-anatomy, commit `caf0f6078f2a0ac9e65e81dce042d5a30b65d0f0`, file `Z-Anatomy.zip` > `Z-Anatomy/Startup.blend`, collection "Muscular system" only.
  Authors: Gauthier Kervyn (design, 3D, anatomy), Marcin Zielinski (Blender add-on), Lluis Vinent (Unity app).
- **"BodyParts3D - The Database Center for Life Science - CC-BY-SA 2.1 Japan"**, the original model that Z-Anatomy adapted.
  Original model: https://dbarchive.biosciencedbc.jp/en/bodyparts3d/download.html (Kousaku Okubo).

The credit text in bold is the wording that Z-Anatomy's `License.txt` asks for ("Please be sure attribute any content copied or derived from the content of this file as follows").

## Licence of this derived model

**SetFlowBody.usdz, SetFlowAnatomy.usdz, SetFlowBody-v1.usdz, SetFlowBody-v2.usdz, SetFlowBody-v4.usdz, SetFlowBody-v5-skin3.usdz, SetFlowBody-v6-skin4.usdz, SetFlowBody-v7-final.usdz, their textures, `muscle_map.json`, `anatomy_map.json` and `variants/` are shared under the Creative Commons Attribution-ShareAlike 4.0 International licence (CC BY-SA 4.0): https://creativecommons.org/licenses/by-sa/4.0/.**

Anyone who redistributes the model, or a model made from it, must give the credit above and use the same licence.

## Changes made (CC BY-SA asks that changes be indicated)

- Only the "Muscular system" collection was used: muscles, tendons and a few aponeuroses and retinacula (linea alba, inguinal ligament, plantar aponeurosis, wrist and ankle retinacula, the digastric's intermediate tendon). Fascia sheets (including the palmar aponeurosis), bursae, joint capsules, intermuscular septa, the platysma, text labels and label anchors were left out.
- Where the external oblique, internal oblique and transversus abdominis sheets lie in front of the rectus abdominis, those faces were removed so the rectus shows.
- Source pieces were merged into one object per muscle and side, renamed (`muscle_<id>_<side>`, `body_detail`, `tendons`), reduced to a low-polygon mesh, and stripped of faces that cannot be seen from outside the body.
- New textures were baked from the source surfaces: a tangent-space normal map and an ambient-occlusion map. The fine muscle-fibre striations in the normal map are procedural (generated during the bake along each source piece's main axis); they are not part of the source data.
- The figure was re-oriented (Y-up, facing +Z) and moved so the origin sits between the feet at floor level.
- Polish pass:
  - Small gaps the source leaves open (nasal opening, ears, orbits, mouth, sternum, spine midline) are closed with plug surfaces made from the source geometry (a morphological closing of the source surfaces).
  - The rhomboids were merged into the trapezius node.
  - The fibre striations of fan-shaped muscles now radiate from each muscle's insertion; they are still procedural.
  - A translucent skin node (`skin`) was added. It is derived from the source surfaces (inflated, remeshed, smoothed) and is not a separate asset.

## Parts excluded for licence reasons

Z-Anatomy's `License.txt` lists two included models under non-commercial licences: "Anatomy of the Inner Ear - by University of Dundee School of Medicine - CC-BY-NC-SA 4.0" and "Kidney - by Lissie Cowley - CC-BY-NC 4.0". Neither is part of the "Muscular system" collection, and the build reads only that collection. The build script also checks every source object name against inner-ear and kidney keywords and stops if one appears. "Cranial Nerves and Foramina" (CC-BY 4.0) and the Brainder and white-matter models are likewise outside the muscular system and were not used.

## Not covered by this notice

The SetFlow app's own code and other assets. The app's licence screen should show the credit above wherever the model appears.

## Skin v3 source (CC0 1.0, no attribution required)

The `skin` node in the current `SetFlowBody.usdz` comes from MakeHuman data files.

**Source.** https://github.com/makehumancommunity/makehuman, commit `a8bc2d54ff0ac92e78ff71431b1023eda42bf482`. Local copy: `downloads/makehuman-a8bc2d54ff0ac92e78ff71431b1023eda42bf482/`, with SHA-256 checksums in `SHA256SUMS.txt`.

**Files used:**
- `makehuman/data/3dobjs/base.obj`;
- the 30 `.target` morph files;
- `makehuman/data/rigs/default_weights.mhw`.

**Licence, re-checked on 2026-10-28:**
- `LICENSE.md` section C: "These assets have been released under CC0 1.0 Universal". The base mesh and targets are listed as assets.
- `base.obj` header: "This asset was explicitly released as CC0 in september 2020".
- All 30 targets carry the same CC0 header.
- `default_weights.mhw`: `"license": "CC0"`.
- `LICENSE.ASSETS.md` holds the full CC0 1.0 legal text.

No MakeHuman program code (AGPL) was downloaded or run; our own scripts read the data files.

**Changes made:**
- Morphed to a lean adult male.
- Posed, and warped onto the Z-Anatomy joints.
- Fitted around the muscles.
- Decimated to 30,000 triangles.
- Given a plain skin-tone material.

CC0 needs no credit. Crediting "MakeHuman (CC0)" is a courtesy.

**Licence of the combined file.** The combined `SetFlowBody.usdz` stays under CC BY-SA 4.0 because of its Z-Anatomy parts. The skin mesh on its own (`work/r2b_skin.blend`) is CC0. `build/variants/SetFlowBody-skin-shell-only.usdz` still holds the older shell made from Z-Anatomy, so it is CC BY-SA 4.0.

## Skin v4 (human body, heat on skin), 2026-10-28

**Source.** Same MakeHuman CC0 data files as skin v3 (`base.obj`, the 30 targets, `default_weights.mhw`, commit `a8bc2d5`). The licence was re-checked as above. No other source was added.

**What is CC0 and what is derived:**
- The skin geometry is MakeHuman's base mesh. It was morphed with MakeHuman targets, posed, and warped onto the Z-Anatomy joints at native resolution.
- The subtle muscle definition in `skinnormal_body.jpg` is baked from the Z-Anatomy muscles, so it is derived from CC BY-SA content.
- The skin region borders (`skin_<group>_<side>`) are computed from the Z-Anatomy muscle positions, so they are derived as well.

**Licence.** The skin-v4 nodes in `SetFlowBody.usdz`, and `variants/SetFlowBody-skin-only.usdz`, are therefore shared under **CC BY-SA 4.0** with the credit above. The MakeHuman mesh on its own remains CC0.

## Final app file, 2026-10-28

No new source was added.
- **`SetFlowBody.usdz` (the app file)** now holds only the 31 skin regions:
  - The geometry is MakeHuman's CC0 mesh.
  - The region borders and the skin normal map are derived from the Z-Anatomy muscles.
  - So the file stays under **CC BY-SA 4.0**, with the credit above.
- **`SetFlowAnatomy.usdz`** holds the Z-Anatomy muscles, `tendons` and `body_detail` (moved out of the app file). With `anatomy_map.json`, it is under **CC BY-SA 4.0**, with the credit above.
- The app's licence screen should show the credit wherever either file is used.

**v8 (2026-10-28).** The new regions `skin_adductors_*` and `skin_tibialis_*` are cut from the same MakeHuman mesh along borders derived from the Z-Anatomy muscles. `SetFlowBody.usdz` stays under CC BY-SA 4.0 with the credit above. No new source was added.
