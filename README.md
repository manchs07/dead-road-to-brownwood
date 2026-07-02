# Dead Road to Ovalo

A *Death Road to Canada*-style zombie road-trip game: **Birmingham, AL → Ovalo, TX.**
Drive west, manage food/gas/medkits, make terrible choices at roadside events, brawl
through scavenge runs and sieges, and pick up the rest of the crew along the way.
Single self-contained HTML file, mobile-first.

## Play
- **Phone / tablet:** open the link in Safari/Chrome → on-screen thumb-stick + buttons.
  Tap **Share → Add to Home Screen** to install it full-screen like an app.
- **Desktop:** double-click `index.html` and use the keyboard.

## Controls
**Touch:** left thumb = move · **HIT** (mash for combos) · **SP** = special (when meter's full) · **DASH** = dodge with i-frames.
**Keyboard:** `WASD` move · `J`/`Space` hit · `K` special · `L` dash · `P` pause · `M` mute.

## The loop
1. **Pick two** — a Leader (★) and a Co-Pilot. Everyone else is stranded on the road ahead.
2. **Drive west** on the map. Every leg burns gas and food (starve = the crew suffers).
3. **Road events** — Buc-ee's jackpots, gas-station sushi, snake farms, tornadoes,
   Longhorns fans, a grandma with casserole. Choices have consequences.
4. **Missions on foot**:
   - **SCAVENGE** — smash crates, grab 🍗⛽✚, get back to the van
   - **HOLD OUT** — survive the siege timer, then mop up
   - **BOSS** — BIG TEX stomps the Dallas fairgrounds; KING RATTLER guards Ovalo
   - **FUEL RUN** — drive on an empty tank and you'll be siphoning under fire
5. **Recruit the crew** — stranded friends join at Meridian, Shreveport, and Abilene (van seats 4; latecomers donate supplies).
6. **Abilene** = hometown siege. **Ovalo** = final boss. Porch = victory.

Downed crew get revived by teammates standing close. Whole crew down = run over.
Weapons (bat, cast iron, machete, chainsaw, guitar) drop from crates and events — they break with use.

## The crew (from the official team slides)
| Fighter | Nickname | Special | Road event |
|---------|----------|---------|-----------|
| **Coyt Hagelstein** | The Coyster | **AUTOFLATULENCE** — stun cloud | Rolls the windows up |
| **Ryan Harp** | Fishstick | **POSTER DUNK** — crater slam | Finds a flight sim |
| **Luke Weems** | Greasy Luke | **FAST DRAW** — shotgun cone | Welds armor onto the van |
| **Ryan Hagelstein** | Ryedawg | **QUASAR CANNON** — LAS-99 beam | Starts a story (it never ends) |
| **Harrison Heger** | Turtle Man | **TURTLE SHELL** — soak & reflect | Spots game (point 45) |
| **Michael Nixon** | Nix | **DEADLIFT SLAM** — hoist & slam | Audits the supplies |

## Adding fighters / events
- **Fighters:** copy a block in the `ROSTER` array (stats, `special`, caricature `face`, `barks`, `joinLine`). New fighters are automatically recruitable on the road.
- **Events:** add to the `EVENTS` array — `{id, title, text, choices:[{label, sub, act}]}`; use `req:()=>inParty('id')` for character-specific ones.
- **Stops:** the `STOPS` array defines the route, gas costs, missions, and recruit points.

## Roadmap
- The rest of the 15+ roster as slides come in (Jeff, Bryce, Greene, Hunter, Zakk, Grayson…)
- Perks/level-ups between stops, trading posts
- 2-player same-screen co-op
- More bosses and arena variety per city
