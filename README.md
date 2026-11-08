# Data Sinners

**They took his water. He took a pitchfork.**

Data Sinners is a darkly comic first-person action game in a cyber-steampunk world. A farmer named John fights the brass-cartoon executives of the Cogitorium, a data center that drained his creek. This repo holds a one-level browser prototype, Level 1: Pump Station Outpost.

- **Play it:** https://perceptivevisions-cpu.github.io/data-sinners/
- **Domain (coming soon):** https://playdatasinners.com
- **Creator:** Jason Lindsey, https://jasonlindsey.art

## The story

John Green's small organic farm, Green Acres, went under after the Cogitorium took the creek to cool its "thinking engines." The county seized his water rights by eminent domain, with $1.00 as "just compensation." His animals had nothing to drink. His wife Jane couldn't take the noise and left, and she took their dog Sprout (a blue heeler) with her. Her note says: *"When the creek returns, so will I."*

The game is about John fighting to get his life back, not just about beating a villain. Every grate he smashes brings a little of the creek back.

**Tone:** darkly comic. The executives are cartoon brass automatons in top hats with cigars and monocles. The world around them is photoreal and weathered. Combat callouts use corporate-speak, for example DOWNSIZED, SYNERGY LOST, PARACHUTE DENIED and VERTICAL INTEGRATION.

**Look:** photographic environments (red barns, rusted iron, dead trees, dry prairie under storm skies) set against cartoon antagonists. The UI is brass, copper pipes and rivets. Fonts are Rye (display), Barlow Condensed (UI), Special Elite and Caveat.

## Level 1: Pump Station Outpost

1. Run the Cogitorium man off John's barn. He's nailing up the seizure notice when the game opens. If you sneak up on him, he's stunned.
2. Smash 4 intake grates. Each is a different puzzle: one runs hot, one is shielded, one is guarded.
3. Wreck the server pods, or jab a pod's red cooling valve and let it cook.
4. Manure stuns anyone. A stunned executive flashes teal; jab him for a glory kill and a canteen of water.
5. The hay-hook yanks enemies in. Pitchfork Fury is the rage mode.
6. A three-phase boss fight finishes the level.

**Enemies:** Executive, Lobbyist, Cloud Consultant, PR Rep, Legal, Boss.
**Weapons:** pitchfork (jab, lunge), manure cannon, hay-hook.

## Running it locally

There's no build step. Everything is in `index.html` plus the image files next to it.

```bash
git clone https://github.com/perceptivevisions-cpu/data-sinners
cd data-sinners
python3 -m http.server 8000
# open http://localhost:8000
```

Use a local server rather than opening the file directly, because browsers block texture loading from `file://`.

## Deploying

Every push to `main` goes live on GitHub Pages within about a minute.

## Credits

Game design, story and art direction: Jason Lindsey. Art is generated with ChatGPT and Adobe Firefly from Jason's prompts, then cleaned up and composited. Code was built in collaboration with Claude.

© Jason Lindsey. All rights reserved. The code and art are viewable here for collaboration and are not licensed for reuse.
