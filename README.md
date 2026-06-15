# Dead Road to Brownwood

A 2D top-down zombie-survival road trip — Jacksonville, FL all the way to Lake Brownwood, TX.
Inspired by *Death Road to Canada*. Single self-contained HTML file, no install, no internet.

## Play
Double-click **`index.html`** — it opens in any browser. To share with friends, just send them that one file.

## Controls
- **WASD / Arrows** — move (your survivor auto-fires at the nearest zombie)
- **Space** (or Shift) — special ability
- **P** — pause · **M** — mute

Survive the drive west. Killing zombies and staying alive fills the route bar at the top.
Reach Lake Brownwood to win.

## Rescue your friends along the road
You pick **one** survivor to drive. The other three are stranded out west — a glowing
beacon and a **HELP! 👋** sign mark each one, with an arrow at the screen edge pointing the
way. Walk into them to pull them into the convoy. Recruited friends trail behind you,
auto-fire at zombies, and have their own health bar (shown in the **CREW** roster, top-left).
If a friend gets swarmed, they go down — with a parting one-liner. Everyone you deliver to
the lake counts on the win screen. Yes, you can even rescue Michael (good luck killing him).

Each survivor is a hand-drawn caricature built from their real photo — backwards cap + beard
for Bryce, Spartan headband for Jeff, aviator shades for Ryan, dad-shades-on-the-forehead for
Michael — plus random in-character trash talk while you drive.

## Tech-demo roster (4 of 15+)
| Survivor | Vibe | Plays like | Special |
|----------|------|-----------|---------|
| **Ryan** | Tall ex-baller, aviation obsessed | Fast, rapid-fire, fragile | **Hangtime Dash** — runway dash w/ i-frames |
| **Jeff Hay** | Strong, Vikings + WWE | Tanky, slow, huge hits | **Skol Slam** — AoE body-slam + knockback |
| **Bryce** | Obsessed Aggie, athletic | Balanced all-rounder | **Gig 'Em Rally** — 12th-Man damage/speed aura |
| **Michael** | Dad-bod, legally Native American, *the creator* | **Cheat character** — invincible, infinite | **Admin Wipe** — vaporize every zombie on screen |

## Adding more survivors (toward 15+)
Open `index.html`, find the `CHARACTERS` array near the top of the `<script>`. Copy a block and edit:

```js
{
  id:'newguy', name:'NAME', color:'#hex', role:'one-line description',
  hp:110, speed:3.6, dmg:30, fireCD:15, range:310, bSpeed:10, pierce:0, knock:6, radius:15,
  weapon:'balanced', bars:{Speed:.7,Power:.7,Health:.65},
  special:{ name:'ABILITY', key:'rally', cd:480, dur:300, desc:'what it does' },
  initials:'N',
  // the caricature — mix and match to match the real person:
  face:{ skin:'#e8b389', hair:'#5b3d27', hairStyle:'short',
         beard:'#5b3d27', beardStyle:'stubble',   // 'none' | 'stubble' | 'full'
         hat:null,                                  // null | 'cap-back' | 'headband'
         hatColor:'#181818', hatColor2:'#c0392b',   // headband stripe (optional)
         glasses:null,                              // null | 'aviator' | 'forehead'
         shirt:'#54447a', cheeks:true },
  barks:["funny line","another quip"],     // random trash talk while driving
  rescueLine:"“said when you pick them up”",
  downLine:"NAME got dropped. RIP."
},
```

- `key` picks the special behavior: `dash`, `slam`, `rally`, or `nuke` (reuse an existing one, or add a new branch in `useSpecial()`).
- `face` is drawn by `drawFace()` — add new hat/glasses styles by extending that function and its `drawCapBack` / `drawHeadband` / `drawAviators` helpers.
- `bars` are just the cosmetic stat bars on the select card (0–1).
- Cards, avatars, the in-game token, the crew roster, and the rescue/recruit flow all build
  themselves from this array — no other edits needed. New survivors are automatically
  rescuable on the road (see `rescueQueue` in `startGame`).

## Roadmap ideas
- The remaining 11+ survivors with their own traits
- Pickups beyond medkits (better weapons, the van itself)
- Boss horde at each city; a final stand at the lake
- Co-op / pass-the-controller party mode
