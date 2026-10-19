# Sprout: design rationale

The same content as the two rationale pages in `docs/screenshots` (pages 12 and 13).

## 1. The story

One continuous journey with the homepage as screen zero. Existing users told us investing feels scary (65%, n=40), most people leave the homepage (78% bounce), and 62% drop off in KYC. Each screen does one job: lower one specific fear, then hand over to the next.

| Step | Feeling | What the user sees |
|---|---|---|
| Homepage | Curious, wary | One promise (₹100, your pace), one button, three small steps |
| 1 and 2 | Prepared | A plain list of what to have ready, and a real way to pause |
| 3 Details | Understood | Every field says why we ask it |
| 4 Verifying | Reassured | A named status, honest timing, and a way to be told |
| 5 Start small | In control | ₹100 minimum, the user picks, risk said plainly |

The mascot grows with the user: a seed when nothing has started, a sprout at welcome, two leaves while work is under way, and a small bud once they are verified and invested. The same mark is the logo, so it is the thread that links the homepage to the last screen.

## 2. How the mascot avoids looking like a cartoon

It is a mark, not a character. It is built from five shapes: a disc, a half-disc of soil, a stem and two leaves. There is no face, no limbs, no outline and no speech bubble. It uses two greens plus ink, with a single amber bud used only when the user is done. Motion is a slow sway (±5° over 4.5 s) and a one-time grow-in, all CSS; with animation off, or when the user prefers reduced motion, the same SVG is held still. It never talks, because the interface carries every word.

## 3. Stakeholder decisions

**The CEO: premium, minimal, no cartoons.** Asked for a premium, minimal look and no cartoons. I used a warm paper ground, deep forest green, hairline borders and generous space, one button per screen, no stock illustration, and a geometric mark instead of a character. Premium in a first-time investor's eyes means calm and trustworthy, not decorated. Minimal also helps the 6.2 s load on 4G, because there are no images, one font family and CSS-only motion.

**Marketing: mascot, video, live ticker, three pop-ups, referral banner.** Asked for five attention-grabbers on the homepage. I kept the mascot (as the mark above) and cut the rest from the homepage. The live ticker is cut because moving prices invite checking and panic, the opposite of the arc we want, and it needs a data feed that adds weight. The three pop-ups are cut because 78% of visitors already leave and each interruption is a new reason to. The video is cut because it is the heaviest asset for the 40% of users on devices under ₹10,000; it can return later as an optional, lightweight "see how it works" behind a poster image. The referral banner moves to one low-priority line on the final "first step is in" screen, where a happy user might act on it and nobody is distracted from starting. The goal is the first investment, so every homepage element has to earn its place against one path to start.

## 4. Compliance checklist

| Constraint | How it is met |
|---|---|
| Risk disclaimer on every investment page, 12 px or larger, visible without scrolling | One shared bar, 12 px on a 1.5 line height, pinned to the bottom of every mobile screen and sticky on desktop. White on ink is 16.24:1. Screen 5 adds a plain-language risk note above the button |
| No banned promise words | Searched all screen copy, microcopy and placeholders. Risk is described as "can go up and down" and "you may get back less than you put in" |
| WCAG AA contrast | All 17 pairs pass. Lowest text pair is 5.62:1 against 4.5:1; controls and graphics are 3.71:1 or higher against 3:1 |
| Tap targets of 44 × 44 px or more | Back 44, chips and list rows 44 or more, steppers 52, fields 54, buttons 56 |
| Page under 1.5 MB, animation under 100 KB each | Designed to the budget: no images, one font family, inline SVG, CSS-only motion under 1 KB. Expected well under 300 KB all-in; to be measured in the build, not yet measured |
| English first, Hindi later | No fixed-width labels, wrapping everywhere, 1.5 to 1.6 line heights, Devanagari fallback, room for about 30% longer text |
| Buildable by one developer in three weeks | Native elements only, no component library. Component list and week-by-week plan are on the type board |

## 5. Accessibility notes

* Real buttons, links, inputs and labels everywhere, so keyboard and screen readers work without extra roles.
* Every field has a visible label, with its "why we ask" line directly beneath.
* Errors are sentences, never colour alone, and announced as alerts.
* Verification status is text first and announced politely as it changes.
* Progress is shown as bars and as words ("3 of 5").
* 3 px focus ring at 6.99:1. Motion stops under reduced motion.

## 6. Hindi readiness

Nothing has a fixed width, so labels, buttons and cards grow with their text and wrap. Body line height is 1.6 and headings 1.2 or more, which keeps Devanagari matras from clipping. The font stack ends in Noto Sans Devanagari so Hindi lands in matching weights. Copy is plain strings, ready to move to a translation file. A sample is on the type board; it still needs a native-speaker review and a visual test at 30% longer strings.

## 7. Testing the copy against the support complaints

* **"I didn't know I needed PAN and Aadhaar."** The homepage says to keep them handy, Welcome lists all three items, and screen 2 is a tick-off checklist with a real "Remind me later".
* **"I thought the app crashed."** Screen 4 always names its state, shows which check is running, gives an honest range ("usually 2 to 5 minutes, sometimes a few hours"), says there is nothing to do, and offers a notification. Loading, slow, error and empty states are all designed.

## 8. My three biggest risks

1. **Verification time is not ours to control.** If a check takes hours, good messaging cannot rescue every user. Mitigation: notify-me with a real SMS or push, and an honest range from the verification provider. Needs a backend commitment.
2. **Minimal may under-explain.** Cutting the video, ticker and pop-ups removes noise, but some visitors may want more proof before they trust a new app. Mitigation: measure bounce against the 78% baseline and add a light "how it works" first.
3. **Regulatory wording is a draft.** The disclaimer, risk note and sample fund text are plain-language drafts. Compliance must approve the exact wording and the PAN and Aadhaar flow. The sample fund is illustrative, not a recommendation.

## Assumptions to confirm

The 10-minute and 2 to 5 minute estimates, the four verification steps, the OTP flow, and the reminder channel (SMS).
