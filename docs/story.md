# The story of Gemma Raus

[← Back to the overview](../README.md) · [How it works](how-it-works.md) · [Principles](principles.md)

---

## The name

*Gemma raus!* is how you say "let's go outside!" in Austria: what you call out when the rain finally stops and everyone has been stuck indoors for too long. That's the moment the app is built for.

## The question

Salzburg is a beautiful city to walk, cycle and sit outside in, and a famously wet one. The *Schnürlregen* can hang over the old town for days, and in summer the storms come off the mountains fast.

Every weather app had an answer for "will it rain today?". None of them answered the question people in Salzburg actually ask, a dozen times a day, at the door: **can I go now, and how long do I have?** A rain percentage for the whole day doesn't tell you whether you can cycle along the Salzach in the next twenty minutes.

## How it started

The first version, in June 2026, was called **SBZ Rain Stalker**. It read one weather model, looked for dry gaps of at least 30 minutes in the next three hours, and showed one of three answers: *GO NOW*, *WAIT 8 MIN* or *STUCK INSIDE*.

It was wrong almost immediately, and in an instructive way. The model it trusted runs about once an hour, and on a fast Alpine storm it reported "partly cloudy, 0.0 mm" while it was pouring outside. A German radar service that looked like the obvious fix turned out to block requests from Austrian networks entirely.

So the app moved closer to the weather. It switched to GeoSphere Austria's own 1 km radar forecast, added the physical rain gauges, and started reading the newest radar image at the user's exact spot. Along the way it got its Austrian name, its own address at [gemmaraus.at](https://www.gemmaraus.at), and the two-lane design that still runs it today: the ground decides *now*, the radar decides *next*.

## Built from real afternoons

Most of what makes Gemma Raus careful came from moments when it wasn't. Every report of a wrong answer gets the same treatment: check it against the live data from that moment, find the real cause, fix it, and turn the moment into a test. A few of those afternoons:

**The hailstorm that read as drizzle (August 2026).** During a thunderstorm with hail in Nonntal, the app said *PASST SCHON*. Two separate safety rules, each sensible on its own, were both listening to the same weather model, which was hours behind the storm, and both quietly turned heavy rain into light rain. Since then, strong radar echoes always get through, and every new rule is checked for what *else* listens to the same signal.

**The rain measured on the wrong clock (August 2026).** On an afternoon of steady rain across the whole city, five neighbourhoods were told to go anyway. The rain gauges report how much fell in 10 minutes; the app's limits were built for 15. Every reading had been coming in a third too low. One conversion fixed it, and the same afternoon taught the app to stop flipping between "stay in" and "go anyway" on every refresh: leaving *BLEIB DRIN* now has to be earned.

**"It's dry and it says WAIT 17 MIN" (September 2026).** A shower over Freisaal, in the south of the city, was being applied to Itzling, five kilometres north and bone dry. With only two gauges near the city, one wet bucket spoke for everyone. Now each gauge only speaks for its own neighbourhood, and everywhere else the radar at your own spot decides.

Each of these is now an automated test built from the real data of that day, one of more than 550. The full record of what changed and why is the most valuable part of the project.

## A short timeline

| When | What changed |
|---|---|
| June 2026 | SBZ Rain Stalker: one model, three answers. |
| June to July 2026 | GeoSphere's 1 km radar forecast, rain gauges and the radar image at your spot. The two-lane design. Renamed **Gemma Raus**, public at gemmaraus.at. |
| July 2026 | Notifications, a thunderstorm watch, and rain approaching with a direction and an arrival time. |
| August 2026 | Storm season. Heavy rain can no longer be talked down; *BLEIB DRIN* has to be earned before it lets go; a "go" now needs a 45-minute window you can actually use. |
| September 2026 | The five-day outlook, the rain ribbon redrawn as tiles, the radar forecast on the map, gauges that speak only for their own neighbourhood, a plain-language privacy policy, and a sun and moon that rise and set on Salzburg's real schedule. |

## Salzburg only, on purpose

Gemma Raus could be stretched to cover more cities. It isn't, for now. Every threshold, clutter rule and storm warning is tuned for an Alpine city with two rain gauges, and copying them somewhere else without the same care would make a worse app, not a bigger one. Salzburg first, and done properly.

## Who's behind it

Gemma Raus is designed and built in Salzburg by **Bestin Antu**. If it got you wet, or kept you dry when it mattered, write to **contact@gemmaraus.at**.

---

[← Back to the overview](../README.md) · [How it works](how-it-works.md) · [Principles](principles.md)
