# Tessy practice studio — anatomical rebuild

## Open locally

Run `npm start` from this directory, then open http://127.0.0.1:4173.

Node.js is needed only for the local HTTP server. Three.js and its loaders/controls are vendored locally. Internet is optional for Google Fonts; system fonts are the fallback. WebGL is required.

## Current character

The active model is `assets/amara-anatomical-v2.glb`. The editable Blender source is `../3D/Amara_Anatomical.blend`. This is a complete anatomical head and shoulder bust, derived from the CC0 MakeHuman hm08 base and explicitly customized morphological targets. It has real facial topology, a continuous neck, separate curved irises and sclerae, fitted brows/lashes, a geometric coiled crop, and a full anatomical UV layout. It does not use the earlier generated-portrait projection or the Gemini model.

Skin has a UV-mapped licensed albedo, a 4096px baked normal map, and a 2048px baked roughness map. The Blender file also retains the procedural skin source material. Normal and roughness detail are portable to the browser. The GLB uses Draco geometry compression and is about 15 MB; its decoder is vendored locally.

**Quality limit:** This is an anatomical character prototype, not a completed hyperrealistic digital human. Dedicated high-resolution head albedo/displacement, a further hair grooming, a physically layered cornea, and further facial detailing remain necessary for photographic close-up quality. The source skin atlas is 2048px for a full body, so its facial colour detail is limited. Do not describe the present model as having achieved the original hyperrealistic brief.

## Working features

- Foundation, blush, eyeshadow, lip colour, contour, and highlight layers.
- Soft UV brush with custom colours, size and build-up controls.
- Mirrored painting via 3D ray reflection; the anatomical UV is not assumed symmetrical.
- Eraser for the selected product layer, 12-step stroke undo/redo, bare-skin comparison.
- Rotation, zoom, three light studies, two jaw studies, tonal studies, placement guides.
- Six text lessons with practice tasks and browser-local reading progress.
- Editable looks stored in IndexedDB; image export opens a portrait preview with a PNG download link and an image-save fallback.

There are no accounts, cloud backups, live payments, subscriptions, video lessons, product-physics simulation, or automatic technique grading. Tonal studies modify one model's texture and do not constitute separate people.

## Verification

- JavaScript syntax checks pass; local HTTP and model routes respond.
- Blender front, three-quarter, and profile clay and material views rendered successfully.
- Browser: model loading, brush stroke, undo/redo state, before/after state, look saving, persistence across reload, and look restoration verified.
- Academy navigation and lesson content verified.
- Lighting selection verified.
- Phone viewport 390px: document width and scroll width both 390px, without horizontal overflow.
- PNG export preview verified separately; automatic download completion could not be confirmed through the in-app browser's download event API.

A look named `Verification · Blush practice` was created during browser QA. It is a local example, not user account data.

## Data and asset revision

Looks stay in this browser's `tessy-anatomical-studio-v2` IndexedDB. Clearing browser data removes them. Lesson progress is localStorage. There is no cloud backup.

The anatomical model uses a new storage namespace because old portrait-projection layers have a different UV layout and cannot be safely reapplied. Rejected files are preserved in `rejected/` and `../3D/rejected/`; they are not loaded by the app.

## Rebuild

1. `python3 scripts/fetch_anatomy.py` retrieves the selected CC0 base/targets and licence.
2. `python3 scripts/fetch_skin_pack.py` retrieves selected CC0 system assets via HTTP byte ranges.
3. Run Blender with `--background --python scripts/rebuild_amara.py` to construct and render the character.
4. Run Blender with `--background --python scripts/export_anatomical.py` to bake/reuse portable maps and export GLB.
5. Run Blender with `--background --python scripts/final_review.py` for larger review views and three review cameras.

Remove old baked maps before rebaking after anatomical or shader changes. Existing maps are deliberately reused for changes confined to eyes/hair, which do not change the skin UV layout. The original procedural script is retained only as rejected development history.

## Licences

See `ASSET_LICENSES.md`. MakeHuman graphical assets are CC0. Three.js is MIT. No MakeHuman application code is incorporated into the web app.
