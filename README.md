# The Dealer Collective — Ring Story Card

A single-page site meant to ship as a QR code with each ring: hero shot,
a personal note, three press-and-hold "stages" (Fit / Form / Weight), and
quick links to email, Vinted trade-in, and Instagram.

## Structure

```
index.html
assets/
  logo.png            crest logo
  hero.jpg            hero photo (hand wearing rings)
  stage-fit.jpg        stage 1 photo (ring sizing)
  stage-form.jpg        stage 2 photo (finished ring)
  stage-weight.jpg      stage 3 photo (ring on scale)
```

No build step — it's plain HTML/CSS/JS. Open `index.html` directly, or
deploy the folder as-is (GitHub Pages, Netlify, S3, etc).

## Personalizing per customer

Since this is meant to be scanned from a QR code, each ring's link can
carry the customer's name without touching the code:

```
https://yourdomain.com/?to=Amara
```

The message section will read "For Amara — this one was made on purpose."
Leave the param off and it falls back to "For you".

## Sound

The press-and-hold sound on each stage is currently **synthesized in the
browser** — a placeholder, not a recorded file, so the interaction is
fully working today with nothing to record or upload yet.

When real recordings exist, open `index.html`, find `SOUND_FILES` near
the top of the `<script>` block, and fill in the paths:

```js
var SOUND_FILES = { fit: null, form: null, weight: null };
// becomes, e.g.:
var SOUND_FILES = {
  fit:    'assets/sound/fit.mp3',
  form:   'assets/sound/form.mp3',
  weight: 'assets/sound/weight.mp3'
};
```

Nothing else needs to change — each stage automatically plays the real
file instead of the placeholder once its path is filled in, and it stays
routed through the same mute control.

## Notes

- The floating Vinted / Instagram buttons currently link to `#` —
  swap in the real profile URLs in `index.html`.
- Contact email is a placeholder: `hello@thedealercollective.com`.
- Fonts (Fraunces, Public Sans, JetBrains Mono) load from Google Fonts;
  everything else is self-contained.
