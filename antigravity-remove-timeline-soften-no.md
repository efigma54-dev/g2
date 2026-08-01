# Task for Antigravity Agent: Remove Photo Timeline + Soften NO-Button Labels

Paste into a new Antigravity task in the same project (`D:\rk\girlfriend-day-website`).
Two targeted changes only — don't touch anything else, including your earlier fixes to
the NO-button roaming logic and the song link-out.

---

## Change 1 — Remove the photo timeline stage (privacy)

We're dropping this stage entirely rather than leaving it optional — it asks for real
photos, and this project may end up in a public GitHub repo, so it's safer to just not
have a photo-upload feature in it at all.

Remove, completely:
- The `<!-- STAGE 3.65: PHOTO TIMELINE -->` `<section id="stage-timeline">` block in the
  HTML, including its `<input type="file" id="timeline-file-input">`.
- The `/* ---------- photo timeline ---------- */` CSS block (`.timeline-track`,
  `.timeline-item`, `.polaroid`, `.polaroid-frame`, `.timeline-caption`, `.timeline-hint`).
- The `CONFIG.timeline` array and its comment block (in the `CONFIG` object near the top
  of the `<script>`).
- The `initTimeline` IIFE in the JS (the block that populates `#timeline-track` and wires
  up the file-picker preview).
- The `timeline:` entry in the `stages` router object.
- The `btn-timeline-continue` event listener.

Then **rewire the flow** so the "continue" button on the phone-mirror stage
(`#btn-phone-continue`) goes straight to `goTo('reasons')` instead of `goTo('timeline')`.
The bouquet → phone → reasons → hug → closing order stays otherwise unchanged.

## Change 2 — Soften the NO-button label progression

Right now the label array repeats "no" in several variants as the button dodges. Replace
it with cuter, pleading phrases that avoid repeating "no" — the tone should read as
"begging nicely," not "refusing."

Find the `const labels = [...]` array inside the `dodgeNo()` function and replace it with:

```js
const labels = ['no','please? 🥺','pretty please?','maybe...?','one more chance?','pookie, please?','just say yes 🥹','so close, come on','yes is right there though','okay fine, say it 😌'];
```

Nothing else about the dodge mechanic (teleport logic, love meter, cupid arrows, screen
shake) changes — this is a one-line array swap.

## Verification

- Confirm the app loads with zero console errors.
- Click through: envelope → question → NO at least 8 times (confirm the label text now
  cycles through the cute phrases above, never showing the old "nope!" / "pookie, no." /
  "no (final answer? lol no)" text) → YES → certificate → bouquet → phone-mirror →
  **continue should land directly on the reasons stage, with no timeline stage in
  between** → reasons → hug → closing → kiss button.
- Confirm there's no dangling reference anywhere to `timeline`, `polaroid`, or
  `stage-timeline` — search the file for those strings after editing and make sure
  nothing turns up.
- Re-check mobile viewport (~390px) and `prefers-reduced-motion` still pass end-to-end.

## Guardrails

- Don't touch the phone-mirror stage, the bouquet/milestone stage, the reasons cards, the
  song link-out you added earlier, or your earlier roaming-button positioning fix.
- Don't re-add any photo/image-upload capability anywhere else as a substitute — the ask
  is to remove it, not relocate it.

## Done when

- The photo timeline is fully gone (HTML, CSS, JS, config) with no dangling references.
- The NO-button label cycle uses only the new cute-phrase array.
- Full click-through reported clean, zero console errors, mobile + reduced-motion both
  still pass.
