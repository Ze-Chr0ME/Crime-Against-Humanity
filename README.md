# Commits Against Humanity

A multiplayer party game in the style of Cards Against Humanity, with developer and version-control themed cards.
It is a single `index.html` published as a claude.ai Artifact. The page uses the Artifact's shared database for lobbies, players and card packs, and its live room to see who is still connected.

## Play

- Open the game's claude.ai link while signed in. Everyone who plays needs edit access to the Artifact, so share it with your friends from the page's **Share** menu.
- Enter a name, then **Create a lobby** and send your friends the 4-letter code, or join one from **Open lobbies**.
- The host sets up the game in the lobby, then starts it once at least 3 players are in.

## Rulers, XP and standings

Each player has a ruler profile, saved per claude.ai account in `profiles/<account id>` (only you can write yours; everyone can read the standings).

- **Portrait**: pick one of 10 species (Mammalian, Reptilian, Avian, Arthropoid, Molluscoid, Fungoid, Lithoid, Machine, Plantoid, Humanoid) and colour the skin, eyes, uniform and backdrop, or upload a picture. Uploads are cropped to a 128 px square JPEG before saving.
- **XP** per round: 10 for playing, 50 when your commit is merged, 15 for judging as czar. Finishing a game adds 40 and winning it 150. Each player's own browser credits them once per round and once per game.
- **Levels and ranks**: level *n* needs 100 + 50 × (*n* − 1) more XP. Ranks go Cadet, Ensign, Lieutenant, Commander, Captain, Commodore, Admiral, Grand Admiral, Galactic Custodian and Galactic Emperor (level 40).
- **Traits** unlock from your stats: First Contact, Silver-Tongued, Arbiter, Prolific, Lucky, Federation Builder, Hegemon, Galactic Veteran.
- **Galactic standings** on the home screen list the top 10 rulers by XP.

## Lobby settings

| Setting | Options | What it does |
| --- | --- | --- |
| Points to win | 3, 5, 7, 10, 15 | The first player to reach it wins. |
| Round limit | none, 5–30 | After the last round, the top score wins (ties share the win). |
| Time to pick cards | none, 30–120 s | When it runs out, the timer plays random cards for anyone who hasn't picked. |
| Time for the czar | none, 30–90 s | When it runs out, a random submission wins the round. |
| Cards in hand | 5, 7, 10 | Hand size for the whole game. |
| Next round starts | after 5, 9 or 15 s, or when the host clicks | Pause on the round result. |
| Max players | 4, 6, 8, 10 | New players can't join a full lobby. |
| Private lobby | on / off | Hides the lobby from **Open lobbies**; friends join with the code. |
| Card packs | any packs in the library | Which prompts and answers are shuffled into the deck. |

Settings are locked while a game is running; the host can end the game to change them.

Opening `index.html` directly or through GitHub Pages only shows a notice, because the multiplayer backend exists only on claude.ai.

## Rules

- Each round one player is the **Card Czar** and the role rotates.
- Everyone else picks a white card (or two or three, on "Pick 2"/"Pick 3" prompts) to complete the black prompt card.
- The czar reads the anonymous submissions and awards the point to the funniest one.
- First player to the target score wins.

## How it works

- The host's browser runs the rules and is the only writer of the lobby document (`lobbies/<CODE>`). Each player writes only their own document (`lobbies/<CODE>/players/<id>`): name, submitted cards and, for the czar, the winning pick.
- A player whose page has been closed for 20 seconds is skipped. If the czar leaves, the round is skipped. If the host leaves, the longest-seated player still connected takes over.
- Players who join mid-game are dealt in at the next round.
- Your player id and current lobby are kept per browser tab, so a reload keeps your seat.

## Card packs

The host picks packs in the lobby. They're grouped, and each group has **All** / **None** buttons:

| Group | Packs |
| --- | --- |
| Base game | Commits Against Humanity (on by default) |
| Expansions | Cloud Bill Shock, Frontend Fatigue, AI Hype Cycle, Gamer Moment |
| Community picks | Sysadmin Sorrows, Data Science Lies, Startup Pitch Deck, Retro Computing, Corporate Feed |
| Trash tier | Internet Meme Pack, Brainrot, Boomer Feed, Dad Jokes, Cursed, Literally Just Bad Cards |
| Made by players | Every pack in the game's shared library |

Cards that appear in more than one selected pack are dealt only once. The bundled packs are in `BUILTIN_PACKS` near the top of the `<script>` in `index.html`; `kind` sets the group they're listed under.

Use **Manage card packs** on the home screen to create, edit, copy or delete packs. Packs are shared with everyone who plays this game; only the person who made a pack can edit or delete it, from the same browser.

- One card per line.
- Write `____` (or any run of 3+ underscores) for each blank in a black card, up to 3 blanks. A black card with no blank is a question answered with one card.
- Up to 400 cards of each colour per pack, 150 characters per card.

The base deck is the `BLACK` and `WHITE` arrays at the top of the `<script>` in `index.html`.

Not affiliated with Cards Against Humanity LLC. All card text here is original.
