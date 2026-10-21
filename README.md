# S N Electrical Services

One-page website for S N Electrical Services (SN Electrical Wrexham Ltd), EV charger installation and domestic electricians in Wrexham.

Plain HTML, CSS and JavaScript in a single `index.html`. No build step and no dependencies.

## Run locally

```
node serve.mjs
```

Then open http://localhost:8085/ (set `PORT` to use another port).

## Placeholders to fill in

Anything the Checkatrade profile didn't give us is shown on the page as a dashed `[Add …]` placeholder.

- **Contact details:** open `index.html` and find the `SETTINGS` block at the top of the main script. Fill in `phone`, `email`, `whatsapp`, `address` and `hours` and the placeholders in the menu and Contact section turn into real, clickable details. A phone number also adds a Call link to the hero and turns the mobile bar's first button into "Call"; an email or WhatsApp number adds a send button to the quote form.
- **About section:** the intro paragraph, Qualified and Insurance rows.
- **Footer:** company number and privacy policy link.
- **Quote form times:** weekdays 09:00–17:00 (`SLOT_FIRST` / `SLOT_LAST`). This is an assumption, not client data.

## Content sources

Everything else comes from the Checkatrade profile https://www.checkatrade.com/trades/snelectricalwrexhamltd (screenshot in `brand_assets/`): rating and sub-scores, the six reviews (verbatim, including typos, cut off where Checkatrade cuts them), NAPIT accreditation, owner name, vetting checks and recent job postcodes. The EV charger photos in `images/ev-*.jpg` were cropped from that screenshot and are low resolution (about 490px wide): swap in originals by replacing the files, keeping the names, or edit the `PHOTOS` array in the script.

The services list is drawn from the job types in the reviews (EV charger installation, EICR, safety checks, extension electrics, certification and remedial work), since only EV charger installation is listed under Skills.

## Site-wide type and motion

Titles and body copy use Space Grotesk (mono is kept for labels and buttons, serif italic for accent words). Section titles rise in word by word, key phrases get a highlighter swipe, big outlined section and card numbers sit behind the content, and cards, facts, steps, photos and contact rows stagger in. Light runs along section edges, the stats strip and the footer. To switch all of it off and get the earlier look back, remove the `sitefx` class from `<body>`. Looping animation pauses when a section is off-screen and everything turns off under `prefers-reduced-motion`.

## Reviews section

The Testimonials section has a bright sky-blue look with motion: a ticker of the words customers use, an animated rating gauge, cards that deal in and tilt toward the mouse, and drifting light and bolts. To go back to the plain pale version, remove the `rvfx` class from `<section id="reviews">`. All of its looping animation pauses when the section is off-screen and turns off under `prefers-reduced-motion`.

## Hero scene

The hero animation is a canvas scene (supply → ECG pulse → wall charger → cable → car). To switch back to the original two-panel circuit scene, change `var SCENE='ev'` to `var SCENE='circuit'` in the hero script. It respects `prefers-reduced-motion` (shows a still frame), pauses when off-screen, and uses lighter settings on low-power devices.
