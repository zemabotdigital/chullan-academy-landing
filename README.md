# Chullan — Academy Landing Page

Landing page for the **Chullan Student Starter Kit** pilot programme, aimed at salon
and makeup academy owners. Its single job is to get an academy owner to book an
intro call on WhatsApp; the product demo is scheduled during that call.

Brand: [chullancosmetics.com](https://www.chullancosmetics.com/)

## Running it

No dependencies, no build step. It is one static HTML file.

```bash
python3 -m http.server 8000
# then open http://127.0.0.1:8000/
```

Or just open `index.html` in a browser.

## Setup before going live

### 1. WhatsApp number (required)

The booking buttons are inert until you add the number. Near the bottom of
`index.html`:

```js
var WHATSAPP_NUMBER = "";   // digits only, with country code: "919876543210"
```

No `+`, no spaces, no dashes. Filling this in wires all four CTAs at once
(header, hero, sticky mobile bar, final section). Until then the buttons stay in
place and show a "number coming soon" notice instead of a broken link.

### 2. First message (optional)

```js
var FIRST_MESSAGE = "Hi Chullan, I'm interested in the Student Starter Kit for my academy.";
```

The rest of the qualifying — academy name, city, batch size, courses, preferred
call time — is handled as tap-buttons inside the WhatsApp flow, not on the page.

### 3. Channel tracking (optional)

`wa.me` links cannot carry UTM parameters, so the page reads them off its own URL
and appends them to the pre-filled message instead:

```
https://your-site.com/?utm_source=instagram&utm_campaign=academy-oct
```

arrives in WhatsApp as `[instagram / academy-oct]` under the first message, so you
can tell which channel sends academies that actually complete the flow.

## Copy that needs sign-off

Two statements on the page are commitments rather than verifiable facts:

- **"One sample kit per academy, sent after the intro call"** — stated in the pilot
  section, the FAQ, and implied by the hero microcopy. Change all three together.
- **"Founding academies, onboarding now"** — implies bookings are open today.

## Structure

Nine sections, in order:

1. Hero — student starter kit angle
2. What's in the Student Starter Kit — the 8-product sequence, framed per student
3. Why academies use it
4. Pilot programme — stands in for social proof; no testimonials, no invented numbers
5. Shade range
6. Standards — IS 4011:2018, IS 14318:1996, SPF 50.8, 40°C stability
7. How booking works — 3 steps
8. FAQ
9. Final CTA

## Notes

- **Design tokens** are taken from the live chullancosmetics.com stylesheet: ink
  `#0e0d0c`, gold `#c9a77b`, paper `#f4f3f0`, with Oswald / Cabin / Jost /
  Instrument Serif.
- **Only external dependency** is the Google Fonts stylesheet. Offline, the page
  falls back to declared stacks rather than breaking.
- **No images.** The page is typographic, which keeps it fast on phones — most
  academy owners arrive from Instagram or WhatsApp on mobile. Product photography
  can be dropped into the hero and the kit grid later.
- Mobile: single column, 54px tap targets, sticky bottom CTA under 1000px,
  safe-area insets for notched phones, `prefers-reduced-motion` honoured.
