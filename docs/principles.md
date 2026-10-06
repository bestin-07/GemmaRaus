# The principles behind Gemma Raus

[← Back to the overview](../README.md) · [How it works](how-it-works.md) · [The story](story.md)

These are the rules every change to Gemma Raus is measured against. They came out of real afternoons in Salzburg, most of them wet ones.

---

## 1. One clear answer beats more data

Six data sources, a dozen rules and a memory all run behind the scenes so that you only have to read **one sentence**. New information is only worth adding if it sharpens that sentence or its countdown. A second number that competes with the headline makes the app worse, however accurate it is.

## 2. Leads are forgiven, lags never

A warning that comes five minutes early costs you five minutes. A warning that comes five minutes late gets you soaked. These are not equal mistakes, and the app is deliberately built to make the first kind instead of the second.

In practice: any rule that hides, softens or delays a warning has to prove it can't make the app late. When the app learned to ignore phantom drizzle on clear summer days, it was only allowed to do so when **two independent witnesses** agreed: the sky was clear *and* the radar image over you was empty. One witness alone is never enough to stay quiet.

## 3. Better you stay in than get sent into the rain

When the gauges say dry but the radar sees light rain right over you, the app says *PASST SCHON*: go, but take a jacket. Occasionally that means a jacket on a day you didn't need one. A jacket beats a soaking.

## 4. The countdown is a promise

Whenever rain is involved, there is exactly one countdown on screen. It is rounded to what the radar can honestly know ("about 25 minutes", not "23 minutes"), it ticks down on your phone between updates, and it doesn't jump when you refresh. A countdown that wobbles reads as broken, even when every individual number was "more accurate".

## 5. Never give an all-clear that our own sources contradict

If the radar is clear but the weather model expects rain later, the app doesn't say "clear for hours". It says "radar clear so far, the model expects rain in about two hours". If the radar forecast is dry but the radar picture over you shows a shower, the app drops its confident timing instead of inventing one. Saying less is always allowed. Saying something one of our own instruments disputes is not.

## 6. The picture and the sentence must agree

What is measured looks different from what is estimated: radar tiles are solid, model tiles are dashed. The headline colour is the same colour as its tile in the rain ribbon. And everything that only *shows* information (the sky glance, the five-day outlook, the map, the banners) is kept strictly apart from the logic that *decides* the answer, so a design change can never quietly change a verdict.

## 7. Change only what is clearly better

Every report of a wrong answer is checked against live weather data before a single line changes: the gauges, the radar, the models, and the airport's own weather report. "Plausibly nicer" is not a reason to change how the app decides. More than once, a proposed tweak was withdrawn within the hour because the live data showed the app had been right.

## 8. Every miss becomes a test

When the app gets it wrong, the real data from that moment becomes an automated test, and the fix has to pass it. More than 550 of these tests now guard the rules, so an old mistake can't sneak back in with a new change.

## 9. Privacy is part of the design

No account, no cookies, no tracking, no ads. Your position stays on your phone: the server sends the forecast for the whole city and your phone picks out your spot. Privacy here is a decision about how the app is built, not a paragraph on a policy page.

## 10. Talk like a friend at the door

The app speaks the way a Salzburger would: *Gemma raus. Passt schon. Bleib drin.* The short lines under the headline come in small rotating sets, so they stay fresh without changing every time you look. No meteorology jargon, no percentages you have to interpret.

---

[← Back to the overview](../README.md) · [How it works](how-it-works.md) · [The story](story.md)
