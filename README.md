# Lotro Delver: Simplified Chinese (zh)

The Simplified Chinese text of [Lotro Delver](https://lotro-delver.com/zh), the fan-made database and toolbox for The
Lord of the Rings Online.

- `frontend/`: the website's text, one JSON file per page or feature.
- `backend/`: text the server writes into tooltips and descriptions (effects, items, quests, instances).

How to translate, the fixed glossary and the style rules are in [`frontend/README.md`](frontend/README.md).

Game terms follow the Chinese translation of the game client by gooslings and team. Thank you!

## Contributing

Corrections and improvements are welcome as an issue or a pull request. Please keep the JSON keys and every
placeholder (`{name}`, `${PLACEHOLDER}`, `%s`, `<tags>`) exactly as they are, and change only the Chinese text.
