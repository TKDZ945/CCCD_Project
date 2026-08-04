# CCCD Website Mockup — GitHub Pages

High-fidelity single-page mockup for **Contra Costa Children's Dentistry** (Walnut Creek, CA).
Six sections — Home, Meet Our Docs, Services, Forms, Contact Us, FAQ — navigated by a sticky top nav with anchor links.

Not the live site. This is for internal review and for handing to Claude Design

## Contents

```
cccd-site/
├── index.html      # entire site: HTML + inline CSS + inline JS
├── images/         # web-optimized JPEGs referenced by index.html
├── .nojekyll       # tells GitHub Pages to serve files as-is
└── README.md
```

## Publishing to GitHub Pages

1. Create a new repo (e.g. `cccd-mockup`).
2. Copy the **contents** of this folder to the repo root — `index.html` must sit at the top level, not inside a subfolder.
3. Commit and push to `main`.
4. Repo → **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main`, folder: `/ (root)` → **Save**.
5. Live in ~1 minute at `https://<username>.github.io/<repo>/`.

If you'd rather keep it private-ish, GitHub Pages on a free account requires a public repo. A private repo needs GitHub Pro/Team.

## Local preview

```bash
cd cccd-site
python3 -m http.server 8000
# open http://localhost:8000
```

Opening `index.html` directly via `file://` also works, but a local server matches how Pages behaves.

## Images

All originals were downscaled to max 1800px and re-encoded at quality 82 — **57 MB → 4.6 MB** total, with no visible loss at display or lightbox size. Keep the untouched originals somewhere safe; these are web copies.

Referenced by the page:

| File | Used in |
|---|---|
| `Ham_Fam.JPEG` | Home hero |
| `Reception_and_Waiting.jpg` | Office tour, stop 1 |
| `Playroom.jpg` | Office tour, stop 2 |
| `Open_Bay.jpg` | Office tour, stop 3 |
| `Consult_Room.jpg` | Office tour, stop 4 |
| `THam_headshot.jpg` | Meet Our Docs — Dr. Tiffany Ham |
| `AHam_headshot.jpg` | Meet Our Docs — Dr. Alex Ham |
| `Infant_1st_visit.jpg` | Services → 1st Visit |
| `Dental_Chair.jpg` | Services → Restorative |
| `Dental_Storyboard.jpeg` | Services → Special Needs |
| `Tooth_Brushing_Itself.JPEG` | Services → Prevention |

Staged but not yet placed — available if you want to fill the remaining placeholder or extend the office tour:

`Front_Desk.jpg` · `Prize_Tower.jpg` · `Play_House.jpg` · `Private_OP2_Hallway.jpg` · `Toy_Tower.jpg`

**Filenames are case-sensitive on GitHub Pages.** `.JPEG` and `.jpg` are not interchangeable — if you rename a file, update `index.html` to match exactly.

### Adding a new photo

Drop the file in `images/`, then put an `<img>` inside any existing `.photo` box:

```html
<div class="photo"><img src="images/Your_File.jpg" alt="Describe it" class="ph" loading="lazy" decoding="async"></div>
```

The `:has(img)` CSS override kicks in automatically — the box drops its fixed aspect ratio and sizes to the image, no cropping. Lightbox and keyboard accessibility are wired up by a MutationObserver, so new images work without touching the JS.

## Design decisions locked in

- **Palette:** lavender `#967BB6` / light purple `#CCCCFF`, dark purple ink `#3B2E52`, soft lavender bg `#F5F2FA`. No green or teal.
- **Type:** Fredoka (headings), Plus Jakarta Sans (body), Space Mono (small labels/data).
- **Photos:** `object-fit: contain`, auto aspect ratio, never cropped. Doctor headshots and the Restorative/Prevention service photos render at 75% width, centered.
- **SEO:** title, meta description, Open Graph, Twitter Card, canonical URL, and `Dentist` JSON-LD all in `<head>`.

## Still open

- [ ] Family/team photo for the "We treat every patient like family" band on Home — the only remaining `<span class="tag">` placeholder.
- [ ] Real bios for Dr. Tiffany Ham and Dr. Alex Ham (both currently bracketed placeholders).
- [ ] Confirm the "Prevention" tab name — the storyboard hinted at a rename that was never clarified.
- [ ] Confirm the Instagram handle (`@cccdentistry`, read off in-office signage) and supply Facebook / TikTok URLs.
- [ ] Replace draft FAQ answers and the Forms intro paragraph with client-approved copy — each is flagged inline with a `✎` note.
- [ ] Decide whether to split into six real HTML pages with per-page SEO metadata for the production build.
