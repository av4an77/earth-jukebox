# Earth Jukebox

## ▶ [Open the live app](https://av4an77.github.io/earth-jukebox/)

**Live app:** https://av4an77.github.io/earth-jukebox/ · **Slides (PDF):** [slides.pdf](https://github.com/av4an77/earth-jukebox/blob/main/slides.pdf) · **Slides (web):** https://av4an77.github.io/earth-jukebox/slides.html

**Listen to our changing planet.** NASA Earth Information Center visualizations, and live NASA satellite imagery that updates itself, turned into music in real time.

Built for the 2026 NASA Space Apps Challenge: *The Earth Information Jukebox*.

## What it does

It works like a jukebox: pick a selection (A1 to A6, B1 to B4), and a needle sweeps the NASA picture from west to east. Every spot of data it crosses becomes a note:

| In the image | In the music |
|---|---|
| Data value, read from the color scale | Pitch, on a musical scale |
| Data category (dust, smoke, sea salt, rain, snow…) | Instrument |
| Brightness | Loudness |
| Change between frames | Rhythm and thunder |
| Whole-frame average | Chord and bass |

Nothing is pre-recorded. All sound is synthesized in the browser from the pixels on screen.

## Tracks

- **Earth Information Center:** sea surface currents (ECCO2), carbon dioxide (GEOS), aerosols (GEOS), lightning from the ISS (LIS), forest height (GEDI), night lights change (VIIRS).
- **Live from NASA GIBS:** Earth Right Now (GOES-East, every 10 minutes), sea surface temperature (GHRSST MUR), rain and snow (GPM IMERG), and monthly air temperature (MERRA-2) with a "Play a whole year" mode. Live tracks open on the newest published image and check for newer data every five minutes. Any past date can be picked too.
- **Your own frame:** drop in any image or video.

## Accessibility

- **Explore mode:** touch, mouse or arrow keys. Each spot plays its note and is described aloud with its location.
- **Sound key:** hear each instrument and what it means (keys 1–4).
- **Spoken captions**, with the music dipping under the voice.
- **Guided tour** of every track (key T).
- **Touch:** tap the picture to play or pause, swipe sideways for the next selection, drag a finger in explore mode.
- **Dial like a jukebox:** press a letter then a number (B then 1).
- Full keyboard control, screen-reader labels, visible focus, reduced-motion support, phone vibration for lightning.

## Run it

It is a static site. Serve the folder with any web server:

```bash
python3 -m http.server 8765
```

Then open http://localhost:8765. (Opening `index.html` directly from disk will not work, because browsers block pixel reads on local files.)

## Files

- `index.html`: the whole app.
- `media/`: NASA SVS visualizations (downscaled or excerpted). `ocean.webm` needs a browser with WebM support (Chrome, Firefox, Edge, recent Safari).
- `slides.html`: 7-slide project demo.
- `SUBMISSION.md`: project write-up.

## Credits and limits

- Imagery: NASA Scientific Visualization Studio / Earth Information Center, and NASA Global Imagery Browse Services (GIBS), part of NASA's Earth Science Data and Information System (ESDIS).
- Values are estimated from each image's color scale, not from the raw science files.
- Code written with the help of Anthropic's Claude.
