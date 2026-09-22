# Project page: Real-Time Force Regulation for Whole-Hand Dexterous Grasping

Static site, no build step. Open `index.html` or serve the folder:

```bash
python3 -m http.server 8765
```

## Deploy to GitHub Pages
Live at https://sangminkim-99.github.io/reactive-grasp-whole-hand/ (repo `sangminkim-99/reactive-grasp-whole-hand`).

Upload the *contents* of this folder to the repo root, not the folder itself, then enable
Settings -> Pages -> Deploy from a branch -> `main` / `/ (root)`.

Videos total about 35 MB, which is fine for Pages, but each re-encode adds another copy to git history.
Avoid committing many video revisions; if the repo grows, move `static/videos` to an external host and
update the `data-src` paths in `index.html`.

## Layout
- `index.html` – the page (hero, authors, highlights, abstract, method, simulation, real world, BibTeX).
- `static/css/index.css` – all styling. Colour and font tokens are at the top.
- `static/js/index.js` – sticky hero stage (full-bleed video collapses into a swipeable slider of the three runs while you scroll), lazy video loading, copy-BibTeX.
- `static/videos/` – web encodes. The real-world runs stay at the camera's native 640x480 (H.264, CRF 20, preset veryslow); upscaling them only costs bytes. About 35 MB in total, lazy-loaded so only the first hero clip is fetched on load.
- `static/images/` – figures cropped from the paper PDF at 220 dpi; `3dv.png` (SNU 3D Vision Lab) and `mit_wordmark.svg` logos; `favicon-32/64.png` and `apple-touch-icon.png`, the hand silhouette traced from a contact rendering with the measured contact heatmap kept on the fingers.

## Sources of the media
| File | Source |
|---|---|
| real_pringles (also the hero) | `Manipulator-Software/recordings/0830_pringles_14/0830_pringles.mp4`, first 4 s removed |
| real_smallbox | `recordings/0830_mouse_box_11/rgb_d455_2.mp4`, first 2 s removed |
| real_largebox | `recordings/0830_block_box_2/rgb_d455_2.mp4`, first 5 s removed |
| real_dorsal (fun grasp) | `recordings/0909_pringles_fun_1/contact_video.mp4`, 32 s to 45 s; RGB cropped to the hand (1144x1068 at 38,0) beside the palmar/dorsal panel |
| method | `~/Documents/ChatGPT/New project/icra2027_supplementary/method_overview_contact_estimation_v23.mp4` (the method segment of the ICRA supplementary video) |
| fig1-8.png | cropped from the paper PDF at 220 dpi, each trimmed to just above its caption |

Contact-heatmap versions of every run exist as `contact_video.mp4` next to each source if you want them back.

## Before going public
- [ ] Enable the two buttons once links exist: point arXiv at the paper and Code at the repository, and drop `is-disabled` plus the "(Soon)" suffix. Fill in the BibTeX (currently "TBA").
- [ ] Confirm the remaining author homepages (Sangbae Kim points at biomimetics.mit.edu; Young Min Kim at 3d.snu.ac.kr).
- [ ] Set `og:image` to an absolute URL once the site has a domain.
- [ ] Optional: add the narrated supplementary video (`ICRA2027_ReactiveGrasping_0916.mp4`) and a button for it.
