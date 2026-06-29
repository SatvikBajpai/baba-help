# बाबा की मदद - Baba Help

A single, self-contained HTML page that runs on one always-on screen for an
elderly, hard-of-hearing grandfather with memory loss. It quietly answers the
two things he keeps asking - "have I eaten?" and "when is everyone coming?" -
and lets the family send him a short note.

There is no build step and no server required: open `index.html` in a browser.

## What Baba sees (always Hindi, numbers in English)

A calm full-screen display that gently rotates between:

- **The time** - big clock, day and date, with a warm greeting by his name.
- **Meals** - whether it's time to eat, or "you've just eaten, your tummy is
  full" with the next meal time, so he isn't anxious and doesn't over-eat.
- **Each family member** - a large photo, their name, and either when they're
  coming (with a countdown) or "यहाँ हैं ✓" if they're at home now.
- **A message** - when the family sends one, it takes over the screen as a big,
  easy-to-read note (he's hard of hearing, so it's shown as text, not spoken),
  for about 10 minutes, then clears itself.

The background warms with the time of day. Text scales to fit any screen
(phone, tablet, or laptop).

## What the family uses (English panel)

Tap the small ⚙ in the corner to open the panel:

- **Log a meal** - one tap when Baba eats; see today's meals.
- **Family members** - add a photo + name; set each person's **daily arrival
  time**, or mark them **At home** (present now). Tap a photo to change it, or
  Delete to remove. Pre-loaded with Sushil (7:00 PM), Shruti (at home) and
  Vishal (8:30 PM).
- **Message for Baba** - tap the mic and **speak in Hindi** (it transcribes to
  text), or just type; **Send to screen** shows it to him, **Clear now** removes
  it early.
- **Settings** - Baba's name and the four **meal times** (Breakfast 8:00,
  Lunch 12:00, Evening tea 4:00 PM, Dinner 7:30 PM by default - all editable).

Everything is saved on the device, so it survives a restart.

## Running it

Simplest: double-click `index.html` to open it in Chrome/Safari.

For the **voice message** feature the microphone needs a secure context, so open
it over localhost instead of `file://`:

```bash
cd baba-help
python3 -m http.server 8000
# then open http://localhost:8000/index.html
```

Typing a message always works, even without the mic or internet. (Chrome's
speech-to-text uses the internet while recording; Safari does it on-device.)

### Set up the always-on screen

Put the device near Baba, open the page, and set the screen to never sleep
(use the browser full-screen / kiosk mode for the cleanest look). The page also
asks to keep the screen awake where the browser allows it.

## Notes

- Photos are compressed in the browser (about 480px) so storage stays small;
  roughly 30+ photos fit comfortably.
- All of Baba's wording is gender-neutral and verb-light, so names read
  correctly for anyone.
- `_build_seed.py` is a one-off helper that baked the starter family photos into
  the page; it isn't needed to run the app.
