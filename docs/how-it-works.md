# How Gemma Raus works

[← Back to the overview](../README.md) · [Principles](principles.md) · [The story](story.md)

Gemma Raus is not trying to describe the weather. It is trying to help you make **one decision about the next few hours**: go now, go anyway, wait, or stay in. Everything below serves that one sentence on the screen.

---

## The problem, in three facts

1. **There are only two real rain gauges near the city.** Within 15 km of Salzburg's centre, GeoSphere Austria runs two active rain gauges: Freisaal (about 1.3 km from the centre) and the Airport (about 3 km). The next one is 19 km away. A shower can fall on Itzling while both gauges stay dry, or soak Freisaal while Itzling is dry.
2. **Radar sees rain that never arrives.** Radar measures echoes in the air. Some of that rain evaporates before it reaches the ground (*virga*). The radar forecast also moves those echoes forward in time, and it is issued 15 to 25 minutes behind real time.
3. **Weather models are late for the Alps.** The big models run about once an hour, and on fast summer storms they can lag two to three hours behind what is actually happening.

No single instrument is trustworthy on its own. So the app never asks one instrument the whole question.

## Two lanes and a memory

### NOW: am I getting wet right now?

This lane trusts the **ground**.

- **The rain gauges** (GeoSphere TAWES, every 10 minutes) are physical buckets that tip when rain actually lands. Once they register rain, they are the most honest number there is. But a gauge only speaks for its own neighbourhood, about 2.5 km around it. Farther away, the radar at your spot is the closer witness, so it decides.
- **The radar picture at your spot** (the newest RainViewer frame, a block of about 700 m around you) catches the drizzle that falls between the gauges. It also tells light echo from a heavy storm core, so it can spot a downpour before a gauge has had time to fill.

### NEXT: when does rain start or stop?

This lane trusts the **radar forecast**.

- **GeoSphere's nowcast** gives rain in 15-minute steps, three hours ahead, on a 1 km grid. The server sends the whole city grid; your phone picks out its own 1 km cell.
- **Light echoes the model doesn't believe in are toned down.** When the weather model gives rain a low chance, faint radar echoes are capped, because that is where virga lives. Strong echoes always pass: a lagging model is never allowed to talk a real downpour down.
- **A break has to be real.** A dry gap must last at least 30 minutes before the app promises it. One 15-minute slot of dry radar is too often noise.
- **A "go" has to be usable.** If a downpour arrives within 45 minutes, or there is no 45-minute dry window anywhere ahead with real rain coming, the answer is *BLEIB DRIN*, even if it's dry this very minute.
- **Rain on its way gets a direction and a time.** The app follows echoes across the last few radar frames, and when one is closing in steadily at a believable speed, you get "rain approaching from the west in about 20 minutes".
- **Beyond three hours, the models take over,** and the ribbon draws them dashed so you can see they are estimates. Two models run side by side (ICON-EU and GeoSphere's AROME), and where they differ, the wetter one is shown. Combining two forecasts can only add warnings, never hide one.

### The memory: keep the story straight

The app remembers what it last told you, on your phone only, and only for the place where it told you.

- If it just said it was raining, a quick re-open doesn't flash "dry" because one reading wobbled.
- If rain just stopped, it says "short break, rain back soon" instead of "rain approaching", which would be the same rain described as something new.
- **Leaving *BLEIB DRIN* has to be earned.** Saying "stay in" too long costs you minutes; saying "go" too early costs you a soaking. So once the app has said *BLEIB DRIN*, it only says "go" when the radar shows a usable dry window, the gauge agrees, and it holds for two updates in a row. To make sure this can only delay good news, never cancel it, the hold lets go after 20 minutes of calm no matter what.

## When the instruments disagree

Every case where the sources disagree is settled by a fixed order of rules. Each rule has exactly one job and one safeguard, and no two rules can flip each other back and forth.

1. **The nearby gauge decides how hard it's raining right now.** If it's measuring rain, that number wins.
2. **A dry gauge doesn't get the last word on drizzle.** If the radar sees light rain right over you, the answer becomes *PASST SCHON*. But a speck on the radar can never on its own push the answer to *WAIT* or *BLEIB DRIN*.
3. **Unless it's a real storm.** An echo that is both heavy and covers the whole area around you can escalate, because two independent signs together are not clutter.
4. **A clear sky vetoes a lone radar speck.** On sunny days, radar picks up reflections off the Untersberg and the Gaisberg. If the model reports a clear sky and only one radar pixel disagrees, the pixel loses.
5. **A downpour coming soon outranks a calm now.** Heavy rain within 45 minutes, or (when it's already raining) steady rain that will drop a millimetre or more on you in the next 45 minutes, turns a "go" into "stay in".
6. **Uncertainty changes the words, never the facts.** When the model isn't sure, the sentence says "rain possible later" instead of a firm time, and at night the wording gets calmer. The colour, the state and the ribbon stay the same.

Over all of them sits one law: **the app never gives an all-clear that one of its own sources contradicts.**

## The countdown promise

Whenever rain is involved, there is exactly one countdown on screen, and it does not jump around:

- **Rounded to 5 minutes** from ten minutes out, and "any minute now" below that. Radar onset times wobble by a few minutes between runs; false precision reads as broken.
- **Ticks every minute on your phone,** between the five-minute data updates, so it never freezes or leaps.
- **One shared forecast for everyone,** fetched once by the server every five minutes, so reloading can't give you a different answer.
- **Never older than 20 minutes.** A stale forecast can't produce a "wait 100 min".
- **The map agrees with the headline.** The dot nearest to you always matches what the big text says.

## Honest limits

- **Very short bursts slip through.** A one- or two-minute burst of rain is shorter than every instrument's delay: the radar picture is 5 to 17 minutes old, a gauge needs 10 to 20, the radar forecast 15 to 25. No app can see that coming, and Gemma Raus doesn't pretend to.
- **Showers are hard to time.** When showers pop up that the radar forecast can't see, the app drops the confident timing and says *SHOWER* instead of inventing an end time.
- **It is tuned for Salzburg.** The thresholds, the clutter rules and the storm warning are calibrated for an Alpine city. Beyond about 50 km, the app shows Salzburg instead of guessing.

## How it checks itself

Every five minutes, the server writes down what the radar forecast predicted for 11 points across the city, 30, 60 and 90 minutes ahead, then checks those predictions against the gauges when the time comes.

It doesn't brag about "accuracy". Rain falls in only a small share of all 15-minute slots, so a forecast that always says "dry" would score above 95 % and be useless. What counts is how much rain was caught, how many alarms were false, and how many showers were missed.

## Under the hood

- **App:** React and Vite, styled with Tailwind, installable as a web app, with a Leaflet map.
- **Server:** Python and FastAPI in a single container. It fetches the shared weather data once per cycle for the whole city, which keeps everyone inside the free limits of the public weather services. That matters because many phones share one IP address on mobile networks.
- **Privacy by design:** your GPS position stays on your phone. The server never receives it.
- **Updates:** a service worker and a version check bring new releases to installed apps without a manual refresh.
- **Notifications:** standard Web Push, opt-in, and only when enough points across the city agree.
- **Tests:** more than 550 automated tests encode the decision rules. Every real-world miss is replayed as a test, so it can't come back quietly.

---

[← Back to the overview](../README.md) · [Principles](principles.md) · [The story](story.md)
