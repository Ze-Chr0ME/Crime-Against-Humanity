# Commits Against Humanity

A party game in the style of Cards Against Humanity, with developer and version-control themed cards.
It is a single static `index.html`: no server, no build step, no dependencies.

## Play

- **Online:** enable GitHub Pages for this repo (Settings → Pages → Deploy from a branch → `main` / root), then open `https://<user>.github.io/olnine_CAH/`.
- **Locally:** open `index.html` in any browser.

## Rules

- Each round one player is the **Card Czar** and the role rotates.
- Everyone else picks a white card (or two, on "Pick 2" prompts) to complete the black prompt card.
- The czar reads the anonymous submissions and awards the point to the funniest one.
- First player to the target score wins.

You play against 2–5 bots. Use **New game** to change your handle, the number of bots and the points needed to win.

## Editing the cards

The decks are the `BLACK` and `WHITE` arrays at the top of the `<script>` in `index.html`.
Write `____` (four underscores) for each blank in a black card; the number of blanks decides how many cards players pick.

Not affiliated with Cards Against Humanity LLC. All card text here is original.
