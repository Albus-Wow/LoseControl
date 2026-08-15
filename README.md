# LoseControl — Conquest of Azeroth Port

> **Enjoying these ports?**
> If they've saved you some time, you can [buy me a coffee ☕](ko-fi.com/albusdev).
> Totally optional — everything here is free and always will be.

---

A port of the classic WotLK **LoseControl** addon, updated to recognise the custom
spells of **Conquest of Azeroth** (Project Ascension's 21-class realm).

CoA's classes are entirely custom content built on top of the 3.3.5 client, using
spell IDs that no stock addon knows about. LoseControl works from a hardcoded
whitelist of spell IDs, so out of the box it simply doesn't react to *any* CoA
crowd control. This port fills that whitelist in.

## What this port adds

- **315 CoA spell IDs** added to the tracking whitelist, covering all 21 classes:
  - 116 CC (stuns + incapacitates)
  - 88 Snares
  - 48 Immunities
  - 32 Roots
  - 31 Silences
- **Interrupt lockout entries** for CoA interrupt abilities
- **Cleanup pass on miscategorised spells** — a number of abilities in the source
  data were tagged as crowd control when they aren't (damage-over-time effects,
  pure stat curses, self-buffs, and cases where a summoned pet or ground-zone's
  *own* lifespan was being read as if it were the CC duration). These were removed
  so they don't fire a false "you are CC'd" alert.

## Known limitations

- **Interrupt lockout durations are approximate.** Unlike everything else here,
  interrupt lockout isn't a readable aura on this client — the addon has to use a
  hardcoded number. The values come from datamined tooltips and may reflect PvE
  rather than PvP durations. Everything else (CC / roots / silences / snares /
  immunities) reads its duration live from the game, so those are always correct,
  including any CC-reduction effects you have.
- **The spell list is not guaranteed complete.** It was generated from datamined
  CoA data, and that data's own categorisation has gaps. If you get hit by
  something and no icon appears, open an issue with the ability name and I'll add it.

## How it works

LoseControl displays a large icon on your screen showing the crowd control
currently affecting you, along with a cooldown spiral and countdown timer, so you
can see at a glance exactly when you'll be free to act again. It also supports
displaying CC on party and arena frames.

Type `/lc` to open the options panel.

## Installation

1. Download and extract
2. Place the `LoseControl` folder into `Interface\AddOns\`
3. Enable **"Load out-of-date AddOns"** on the character select screen if it
   doesn't appear in your addon list
4. `/reload` or restart the game

## Credits

All credit for the original addon goes to **Kouri** and contributors — this port
only adds a spell list for CoA content and does not change how the addon works.

- Original addon: LoseControl by Kouri et les potos
- WotLK 3.3.5 base used for this port: [wotlk-addons/LoseControl](https://github.com/wotlk-addons/LoseControl)
- CoA spell data sourced from [johnayoung/coa-arena](https://github.com/johnayoung/coa-arena)

This port is not affiliated with or endorsed by the original authors, Project
Ascension, or Blizzard Entertainment.
