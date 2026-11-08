# Brief for AI assistants (Claude, ChatGPT, Cursor, Copilot, etc.)

Read this and README.md before changing anything. README.md has the story, tone and level design. This file covers how the project works and how Jason wants it worked on.

## Who's who

- **Jason Lindsey** owns the game. He's a filmmaker and photographer, not a programmer. He directs, writes the story and makes most of the art. He's very picky about visual design; anything generic or "free-app" looking is wrong.
- Collaborators and their AIs work under Jason's direction. Creative calls (story, look, feel, names) are his.

## How Jason wants to work. Follow these rules.

1. **Talk it through before building.** Propose the plan, get a yes, then build. Don't run off and execute a big change unprompted.
2. **Build on the existing prototype.** Never rebuild from scratch; he rejected a from-scratch rebuild once already. Extend and patch what's here.
3. **Only change what was asked.** Don't touch approved elements while fixing something else.
4. **Keep it to one level until it's dialed in.** Going too big too fast is the mistake to avoid. Polish Level 1 before adding levels.
5. **Aim for the real standard.** Compare against successful commercial web games (Krunker, Vampire Survivors, Slither.io), never "good enough for a prototype."
6. **Test small, then apply.** Show a short sample or one section before changing the whole game.
7. **Feel is the priority.** The combat overhaul (hit reactions, burst-apart deaths, combos) was the first point Jason felt "addicted" playing it. Protect that feel.

## Decisions already made (don't reopen without asking)

- The game opens at the barn, with John fighting the executive who's nailing up the notice. The old farm-walk prologue (reading notes around the farm) was cut as boring.
- The opening cinematic is about 35 seconds of Jason's painted stills (`cine_c*.jpg`) with Ken Burns camera moves. A separate "Cogitorium commercial" style intro, cut in Premiere, lives on the itch.io page, not in the game.
- The core emotional arc: John lost Jane and Sprout and is fighting to get them back. An idea under consideration: Sprout is caught by the Cogitorium and Level 1 ends in a rescue.
- Art stays 2D sprites/cutouts in a 3D world for now. 3D models come later.
- Phone play matters as much as desktop. There's a full touch-control layout, and it can be installed as a home-screen app via `manifest.json`.

## Code map

There's one file, `index.html` (about 1,700 lines). It has no build step and no framework.

- **Engine:** Three.js r128 from cdnjs. Fonts come from Google Fonts.
- **Screens (HTML):** `#title`, `#howto`, `#about`, `#pause`, `#dead`, `#end`.
- **World:** `SKY`, `START`, `FARM_START`, `PIPE_START`, `layWater` (the living creek that refills as grates fall), `building`, `cutout`, `propS`/`propP` (billboarded photo props), `scatter`, `placeBale`, `TREES`, `SOIL`.
- **Server cabinets:** `cabinet`, `makeRack`, `ledTex`, `tickCabs` (blinking lights from the `cab_*_l.webp` light layers).
- **Enemies:** `KIND` (stats per type), `WAVES` / `POD_WAVES`, `spawnExec`, `POSE` / `setPose` (hit-reaction sprites `p_*.webp`), `burstApart` / `spawnChunk` (death pieces from `parts.webp`), `flyHat`.
- **Player combat:** `jab`, `dodge`, `hook`, `fireCannon` / `dropManure`, `gloryKill`, `parry`, `addFury` / `unleash` (Pitchfork Fury), `hurt`.
- **Puzzles and objectives:** `hitGrate` / `destroyGrate` / `coolGrate` / `setHot` / `resetPuzzles`, `hitValve`, `hitRack`, `pullLever`, `bossDown`.
- **Scoring and juice:** `addScore`, `breakCombo`, `callout` with `CALL` (corporate-speak callouts), `popAt` (floating numbers), `drawCracks` (low-health screen cracks), `MEDALS`, best scores in `localStorage` key `ds_best`.
- **Audio:** everything is synthesized in Web Audio with no audio files: `audioInit`, `music` (builds with the combo multiplier), `sfx` / `sfxAt` (positional), `unlockIOSAudio`.
- **Settings:** `SET`, saved in `localStorage` key `ds_settings`.

## Assets

- `cine_c*.jpg`: opening cinematic stills
- `ex*.webp`, `exec*.png`, `exec_nail.webp`, `exec_turn.webp`, `p_*.webp`, `parts.webp`: executive sprites, poses and death pieces
- `f_*.webp`, `h3_*.webp`, `b3_*.webp`: farm, house and barn cutouts
- `cab_*.webp`: steampunk server cabinets and their light layers
- `fence*`, `gate*`, `tree*`, `grass*`, `bale_*`, `barrel`, `barrow*`, `wagon*`, `wheel`, `windmill*`, `post*`, `sack*`: props
- `t_*.jpg`, `g_*.jpg`, `roof_*.jpg`, `mud.jpg`, `grass.jpg`: tiling textures
- `sky*.jpg`, `drift*.png`, `fortress.png`: sky, clouds and the Cogitorium on the horizon
- `ui_*.webp`, `logo_*.webp`, `icon*`: brass UI frame and buttons, logo, app icons
- `notice.webp`, `photo*.webp`, `canteen.webp`, `muffs.webp`: story props and pickups

**Art pipeline:** Jason generates images in ChatGPT or Firefly, usually from his own prompts. They get background-removed, cropped and compressed to WebP, then wired into the code. To ask Jason for new art, write him a specific image prompt that matches the existing style.

## Workflow

- Work on a branch and open a pull request. Don't push straight to `main`, because `main` goes live immediately on GitHub Pages.
- Test on a phone as well as desktop before merging.
- Keep it a single self-contained `index.html` unless Jason agrees to restructure.
