# Earth Jukebox: Space Apps 2026 submission text

Paste each section into the matching field on your team's Project page.
Deadline: **Sunday Nov 15, 11:59 p.m. local time** (your Local Event's time zone).

---

## Project name
Earth Jukebox: Listen to Our Changing Planet

## Challenge
The Earth Information Jukebox

## High-level summary (short field)
Earth Jukebox is a web app that turns NASA Earth Information Center visualizations, and live NASA satellite imagery that updates itself, into music as they play. It works like a real jukebox: you pick a selection such as A3 or B1, a needle sweeps the picture from west to east, and every spot of data it crosses becomes a note: the value read from the image's color scale sets the pitch, the data category sets the instrument, brightness sets the loudness, and change between frames drives the rhythm. On NASA's aerosol map, Saharan dust plays as horns, fire smoke growls, sulfate pollution is plucked and sea salt rings like bells. On the live rain map for 19 August 2025 you can find Hurricane Erin by ear. Blind and low-vision users can touch any spot, or move with the arrow keys, to hear it and have it described aloud. The live tracks start on the newest image NASA has published and check for newer data every five minutes, so the music changes as the planet does. A sound key teaches each instrument, a guided tour narrates every track, and "Play a whole year" lets you hear the seasons swing across the planet. Every sound is computed live from NASA pixels in the browser, so Earth science reaches people through their ears as well as their eyes.

## Project details

**What it does**

Ten tracks in three groups:

- **Earth Information Center (NASA SVS):** ECCO2 sea surface currents and temperature, DYAMOND global CO₂, GEOS aerosols (19 Aug 2025), ISS LIS lightning, GEDI forest height, and VIIRS night-lights change 2012–2023.
- **Live from NASA satellites (NASA GIBS).** Each one opens on the newest image NASA has published, checks for newer data every five minutes and updates the picture and the music by itself. You can also pick any past date.
  - Earth Right Now: the Americas from the GOES-East weather satellite, a new image every 10 minutes (usually one to three hours behind real time).
  - Sea surface temperature (GHRSST MUR), daily.
  - Rain and snow (GPM IMERG), hourly steps, about a day behind real time.
  - Air temperature (MERRA-2), monthly, with a **Play a whole year** button that steps through all 12 months so you hear the warm band move north and south with the seasons.
- **Your own frame:** drop in any image or video (for example a frame saved from NASA SVS) and hear it. The file never leaves the device.

How the sound is made:

| Visual | Sound |
|---|---|
| Position west → east | Time. The playhead sweeps the frame once every 2 bars |
| Data value read from the image's color scale | Pitch, snapped to a musical scale so it stays listenable |
| Data category (dust / smoke / sulfate / sea salt; snow / light rain / heavy rain) | Instrument |
| Brightness and saturation | Loudness and tone |
| Change between frames | Percussion. Sudden flashes become thunder, plus a phone vibration |
| Whole-frame average | Background chord and bass. Higher CO₂ adds dissonance |
| Left ↔ right, top ↔ bottom | Stereo position, register |

Accessibility is the core of the design:

- **Explore mode:** touch, mouse or arrow keys move a listening cursor. Each spot plays its note and is described aloud with its location, for example "heavy rain, high. Near 25°N, 72°W."
- **Sound key (auditory legend):** press a button, or keys 1 to 4, to hear each instrument and what it stands for.
- **Spoken captions** summarise what is playing, and the music dips under the voice so the words stay clear.
- **Guided tour:** one key press plays every track with a spoken introduction.
- **Touch first:** tap the picture to play or pause, swipe sideways to change selection, drag a finger to explore. Every control is at least 48 pixels tall, with a small vibration on press where the phone supports it.
- **Dial a selection** with a letter and a number, like a real jukebox.
- Full keyboard control, screen-reader labels and live regions, a skip link, visible focus, and reduced-motion support.
- **Record:** save any sonification as an audio file.

**How we built it**
- One static web page: HTML Canvas reads the pixels, and the Web Audio API synthesizes every instrument (bells, plucked strings, horns, growls, sparkles, thunder, pads and bass) with reverb and a lookahead scheduler.
- The Web Speech API provides narration and the Vibration API provides haptics.
- Each frame is sampled on a 32 × 12 grid. For every cell we keep the most striking pixel, so small features such as city lights or one lightning flash are not averaged away.
- Each dataset has its own color-to-value reader, checked against NASA's published color keys and descriptions.
- Live imagery is requested from NASA GIBS (WMS). To find the newest data, the page sends tiny probe requests for recent time steps and picks the latest one that contains data. It repeats this every five minutes and when you return to the tab.
- No server, no third-party libraries, no audio samples.

**Why it matters**
Visualizations are the main way NASA shares Earth science, and they do not reach the roughly 2.2 billion people living with a vision impairment (WHO). Sound also carries pattern and emotion in a way a map does not: you can hear the dust plume cross the Atlantic, the tropics drum with lightning, and the seasons breathe. Earth Jukebox could run in the Earth Information Center itself, in museums and classrooms, and on any phone.

**Validity and limits**
- Values are estimated from each image's color scale, not from the raw science files. The app states this on screen.
- The sound was checked by inspecting what the audio engine schedules for each dataset. It has not yet been tested with blind and low-vision listeners.
- Next steps:
  - Read the underlying NetCDF data through NASA Earthdata so pitch maps to exact physical values.
  - Run listening tests with blind and low-vision users.
  - Add more GIBS layers and a spoken numeric legend (°C, mm/hr, ppm).

## Use of AI (Super Intelligence) — required field
Yes. This project was built with heavy use of an AI coding assistant (Anthropic's Claude). Claude helped shape the project idea and the sonification design (how data values, categories, brightness and change map to pitch, instrument, loudness and rhythm), reviewed the challenge resources, wrote and debugged all of the code (pixel sampling, Web Audio synthesis, scheduler, live-data updating, accessibility features), and drafted this write-up and the slide deck. I directed the work, asked for the live self-updating NASA data, and reviewed and tested the result. The code carries an AI-assistance note in its metadata, page footer and README. Color keys were checked against NASA's SVS and GIBS descriptions. No AI-generated images, video, music or voices are used: all imagery is NASA's, all sound is synthesized live from it by the app's code, and spoken captions use the device's built-in text-to-speech. No NASA branding or logos were generated or modified.

## NASA data used
- Earth Information Center content database: https://svs.gsfc.nasa.gov/gallery/earth-information-center/
- Global Sea Surface Currents and Temperature (ECCO2): https://svs.gsfc.nasa.gov/3912/
- DYAMOND Global Carbon Dioxide (GEOS): https://svs.gsfc.nasa.gov/5196/
- GEOS Aerosols (2025): https://svs.gsfc.nasa.gov/5669/
- Lightning Events Detected from the ISS 2017–2023 (LIS): https://svs.gsfc.nasa.gov/5011/
- GEDI Forest Height: https://svs.gsfc.nasa.gov/4950/
- Change in Night Lights between 2012 and 2023, EIC Version (VIIRS): https://svs.gsfc.nasa.gov/5313/
- NASA Global Imagery Browse Services (GIBS): https://gibs.earthdata.nasa.gov/ — layers `GOES-East_ABI_GeoColor` (satellite operated by NOAA), `GHRSST_L4_MUR_Sea_Surface_Temperature`, `IMERG_Precipitation_Rate`, `MERRA2_2m_Air_Temperature_Monthly`, `Coastlines_15m`
- Conceptual reference: Data Sonification: Caldwell 73: https://svs.gsfc.nasa.gov/13786/

## References (external resources)
- NASA Scientific Visualization Studio imagery (credit NASA SVS / Goddard Space Flight Center)
- NASA GIBS imagery: "We acknowledge the use of imagery provided by services from NASA's Global Imagery Browse Services (GIBS), part of NASA's Earth Science Data and Information System (ESDIS)."
- World Health Organization, vision impairment fact sheet (2.2 billion figure)
- MDN Web Docs: Web Audio API, MediaRecorder, Web Speech API
- Anthropic Claude (AI coding assistant)
- No third-party code libraries, music samples or copyrighted media.

## Demo
You need one: a 30-second video **or** up to 7 slides.

- **Slides (ready, after you add your names):** `slides.html` in this folder is a 7-slide deck. The rules require the team name, member names and challenge on the slides, so replace the two placeholders on slide 1 first. Open it in a browser and use File → Print → Save as PDF, then upload or link the PDF.
- **Video (stronger, if you have 10 minutes):** a 30-second screen recording with sound. Script:

| Time | Show | Say / caption |
|---|---|---|
| 0–4s | Start screen, then press Play on GEOS Aerosols | "What does our planet sound like?" |
| 4–11s | Playhead crosses Africa and the Atlantic | "Every pixel of NASA data becomes a note. Dust is horns, smoke growls, sea salt rings like bells." |
| 11–17s | Live track "Rain and Snow", Explore mode, tap the hurricane | "Touch anywhere to hear it. This is Hurricane Erin, found by ear." |
| 17–25s | "Earth Right Now", showing the "Newest from NASA" time stamp | "It plays the newest satellite image and updates itself as NASA publishes more." |
| 25–30s | Lightning track | "Earth Jukebox. NASA Earth science for every sense." |

On macOS: **Cmd+Shift+5 → Record Selected Portion**. macOS does not capture the computer's own sound by default, so either hold the laptop's speakers up (set Options → Microphone → built-in), or record on a phone pointed at the screen.
