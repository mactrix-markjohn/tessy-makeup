# Asset provenance and licences

## Anatomical base and shape targets

- Source: https://github.com/makehumancommunity/makehuman
- Base mesh: `makehuman/data/3dobjs/base.obj` (hm08).
- Graphical asset licence: CC0 1.0. The repository's application code has a separate licence and is not incorporated here.
- Licence statement: https://github.com/makehumancommunity/makehuman/blob/master/LICENSE.md
- Local licence copy: `source-assets/makehuman/LICENSE.md`.
- Local source list: `source-assets/makehuman/sources.json`.
- Morph recipe and all weights: `scripts/rebuild_amara.py`, also embedded as a custom property on the native face object.

## Skin, fitted brows and lashes

- Source pack: https://files.makehumancommunity.org/asset_packs/makehuman_system_assets/makehuman_system_assets_cc0.zip
- Official asset list and licence: https://static.makehumancommunity.org/assets/assetpacks/makehuman_system_assets.html
- Assets used: young African female diffuse skin, eyebrow001, eyelashes01; graphical assets CC0.
- Original data retained under `source-assets/system-assets/`.
- Derived normal and roughness maps: authored procedural microstructure baked in Blender.

## New authored components

- Iris and pupil geometry/material data, scleral geometry, coiled hair fibres, scalp fitting, character recipe, studio, application code: authored for this project.
- The character is fictional. Nigerian identity is creative context, not a claim that nationality can be determined from a facial shape.
- User-supplied reference photos are not mapped onto this model.
- Earlier AI portrait and failed procedural mesh are archived and are not used by this rebuild.

## Application library

Three.js 0.160.0, MIT. Copyright notice and licence are retained in `vendor/THREE-LICENSE.txt`.

## Mesh decoder

Draco decoder bundled with Three.js, from Google Draco (Apache 2.0). Its licence is retained in `vendor/draco/LICENSE`. The browser uses locally served decoder files; no external decoder CDN is needed.
