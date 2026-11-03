# Licence notice: SetFlowBody.usdz

`SetFlowBody.usdz` and `muscle_map.json` in this folder are the app file from the SetFlow model build (`build/BUILD-REPORT.md`, "v8: inner-thigh and shin regions", 2026-10-28; map version `2026-10-28-v8-regions`, schema 3).

The file combines two sources:
- the body surface, from MakeHuman under CC0 1.0 (below);
- the region borders and a subtle normal map, derived from Z-Anatomy and BodyParts3D under CC BY-SA 4.0 (below).

Because of the derived parts, the file is shared under CC BY-SA 4.0 and needs the credit below.

## Credit (required)

This 3D model is derived from:

- **"Z-Anatomy - The libre 3D atlas of anatomy - CC-BY-SA 4.0"**
  Source: https://github.com/Z-Anatomy/Models-of-human-anatomy, commit `caf0f6078f2a0ac9e65e81dce042d5a30b65d0f0`, file `Z-Anatomy.zip` > `Z-Anatomy/Startup.blend`, collection "Muscular system" only.
  Authors: Gauthier Kervyn (design, 3D, anatomy), Marcin Zielinski (Blender add-on), Lluis Vinent (Unity app).
- **"BodyParts3D - The Database Center for Life Science - CC-BY-SA 2.1 Japan"**, the original model that Z-Anatomy adapted.
  Original model: https://dbarchive.biosciencedbc.jp/en/bodyparts3d/download.html (Kousaku Okubo).

The credit text in bold is the wording that Z-Anatomy's `License.txt` asks for ("Please be sure attribute any content copied or derived from the content of this file as follows").

## Body surface (CC0 1.0, no attribution required)

The body mesh comes from MakeHuman data files: https://github.com/makehumancommunity/makehuman, commit `a8bc2d54ff0ac92e78ff71431b1023eda42bf482`.
- Files: `makehuman/data/3dobjs/base.obj`, 30 `.target` morph files and `makehuman/data/rigs/default_weights.mhw`.
- Licence, checked 2026-10-28: `LICENSE.md` section C ("These assets have been released under CC0 1.0 Universal"); the `base.obj` header ("This asset was explicitly released as CC0 in september 2020"); the same CC0 header on all 30 targets; `"license": "CC0"` in `default_weights.mhw`.
- No MakeHuman program code (AGPL) was used; the build's own scripts read the data files.

Crediting "MakeHuman (CC0)" is a courtesy, not a requirement.

## Licence of this file

**SetFlowBody.usdz, its texture and `muscle_map.json` are shared under the Creative Commons Attribution-ShareAlike 4.0 International licence (CC BY-SA 4.0): https://creativecommons.org/licenses/by-sa/4.0/.**

Anyone who redistributes the model, or a model made from it, must give the credit above and use the same licence. The MakeHuman mesh on its own remains CC0.

## What is derived, and the changes made (CC BY-SA asks that changes be indicated)

- The MakeHuman base mesh was morphed with MakeHuman targets to a lean adult male, posed, and warped onto the Z-Anatomy figure's joints, at native resolution.
- It was split into 35 opaque skin regions: one per region group and side (`skin_<group>_<side>`, 30), plus the head, both hands and both feet (5). The 15 region groups are the app's 13 muscle groups plus `adductors` (the upper inner thigh) and `tibialis` (the front of the shin). Each face takes the group of the Z-Anatomy muscle under it, and the borders are cut along smoothed curves. **The region borders are derived from Z-Anatomy.**
- The adductor and tibialis regions follow the Z-Anatomy adductor muscles (longus, brevis, magnus, pectineus, gracilis) and tibialis anterior with the long toe extensors; they take their area from the quads and calves regions, and every other region keeps its shape. `muscle_map.json` folds them into quads and calves for the app (`folded_groups`), so the app colours and opens them with those groups.
- A subtle tangent-space normal map (broad pectoral, deltoid and abdominal relief) was baked from a smoothed envelope of the Z-Anatomy muscles and tendons. **The normal map is derived from Z-Anatomy.**
- The Z-Anatomy muscle figure itself is not in this file, and the app does not bundle it.

## Parts excluded for licence reasons

Z-Anatomy's `License.txt` lists two included models under non-commercial licences: "Anatomy of the Inner Ear - by University of Dundee School of Medicine - CC-BY-NC-SA 4.0" and "Kidney - by Lissie Cowley - CC-BY-NC 4.0". Neither is part of the "Muscular system" collection, and the build reads only that collection. The build script also checks every source object name against inner-ear and kidney keywords and stops if one appears.

## Not covered by this notice

The SetFlow app's own code and other assets. The app's licence screen (Settings > Acknowledgements) shows the credit above.
