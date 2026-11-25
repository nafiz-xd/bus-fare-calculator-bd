# Bus Fare Calculator BD

Work out the correct bus fare for any trip in Bangladesh, using the real BRTA per-kilometre rates. The result is shown as a bus ticket stub, with a full breakdown of how the fare was worked out.

**Live demo: https://nafiz-xd.github.io/bus-fare-calculator-bd/**

## Rates used (BRTA gazette, effective 22 September 2026)

| Service | Per km | Minimum fare |
| --- | --- | --- |
| City bus — Dhaka & Chattogram | ৳2.70 | ৳10 |
| City minibus & DTCA-area bus/minibus (Dhaka, Narayanganj, Munshiganj, Narsingdi, Gazipur, Manikganj) | ৳2.60 | ৳8 |
| Inter-district / long-distance bus & minibus | ৳2.40 | — |

**Honest limits:** these rates are for **diesel buses only** — gas-run (CNG) buses are not covered. AC and premium buses, tolls and terminal charges are extra. The app adds any toll you enter in full; it never discounts the toll.

## How the fare is worked out

1. Base fare = distance × per-km rate.
2. Minimum-fare floor applied where one exists (city ৳10, minibus/DTCA ৳8).
3. 40-seater buses on long routes: fare × 51/40 (real BRTA rule — optional toggle).
4. Student half fare (BRTA rule — optional toggle): the bus fare is halved.
5. Toll / bridge charge added in full.
6. The bus fare is rounded to the nearest whole taka (৳0.50 rounds up) before the toll is added.

Worked examples:

- 10 km city bus: 10 × ৳2.70 = ৳27.
- 2 km city bus: 2 × ৳2.70 = ৳5.40, raised to the ৳10 minimum.
- 10 km city bus, student: ৳27 ÷ 2 = ৳13.50 → **৳14**.
- Sayedabad–Chattogram, 242 km inter-district: 242 × ৳2.40 = ৳580.80 → ৳581, plus ৳450 toll = **৳1,031**.

> **Note on the Chattogram route:** BRTA's published figure for Sayedabad–Chattogram is ৳552 + ৳450 toll, but that was calculated at the old ৳2.23/km rate. This app uses the **new ৳2.40/km rate** from the 22 September 2026 gazette, so it shows ৳581 + ৳450 = ৳1,031. If BRTA republishes a rounded route fare at the new rate, that printed figure is final.

## Features

- Route type selector (city bus / city minibus–DTCA / inter-district), distance in km, optional toll, student half-fare toggle, 40-seater toggle
- Full fare breakdown: km × rate, minimum-fare floor, 40-seat adjustment, student half, toll, total
- Popular-route presets with real distances from BRTA fare charts: Gulistan–Gazipur 41.5 km, Mirpur Zoo–Keraniganj 21 km, Sayedabad–Chattogram 242 km (toll ৳450), Sayedabad–Cumilla 102 km, Sayedabad–Sylhet 257 km, Gabtoli–Barishal 242 km (ferry fare extra, not included)
- Recent calculations saved in the browser (localStorage) with a history list and clear button
- Fare-table reference in the app, so it doubles as a rate card
- Bus-ticket-stub result design with a perforated edge; works on small phones (no overflow at 360px)

## How to use

1. Pick the route type.
2. Enter the distance in km (or tap a popular route).
3. Add any toll, and turn on the student or 40-seater options if they apply.
4. Tap **Calculate Fare** — the ticket shows the total and every step of the maths. Tap **Copy fare** to copy it.

## Tech

Single `index.html` — vanilla HTML, CSS and JavaScript, no dependencies, no build step. History lives only in your browser's localStorage; nothing is sent anywhere.

---

Built by Nafiz Bin Azad
