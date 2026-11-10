# 📘 Pokémon Binder Locator

> Find any Pokémon's exact page and slot in your binder — instantly.

A free, lightweight tool for Pokémon TCG collectors. No account needed, no internet required after loading, no data ever leaves your device.

![Static Badge](https://img.shields.io/badge/version-1.0.0-7B2FBE)
![Static Badge](https://img.shields.io/badge/languages-PT%20%7C%20EN%20%7C%20JP-success)
![Static Badge](https://img.shields.io/badge/storage-local%20only-blue)
![Static Badge](https://img.shields.io/badge/dependencies-zero-lightgrey)

---

## ✨ Features

- **Instant search** — type a partial name (`pika` → Pikachu) or Pokédex number
- **Autocomplete** with Pokémon sprites fetched live from PokéAPI
- **Auto-save** — selecting a Pokémon saves it to your collection automatically
- **My Binder** — visual two-page spread view, like a real open binder (empty slots shown faded)
- **Go to Binder (📍)** — jump from any entry straight to its page in My Binder and highlight the slot
- **Binder size** — 2×2, 3×3 or 4×4 pages; positions, statistics and the binder view all follow the chosen size
- **Front/Back mode** — supports physical sheet tracking (front = odd pages, back = even pages)
- **Generation filter** — filter by National Pokédex or any generation (Gen I–IX)
- **Collection filters** — view All / Have / Missing across the full Pokédex
- **Statistics** — total, occupied pages, complete pages/sheets, complete generations, **complete evolution lines** (e.g. Squirtle + Wartortle + Blastoise = 1), **completion % donut** for the selected Pokédex, last 5 added, and missing ranges
- **Import / Export JSON** — back up and restore your collection
- **Custom Pokédex import** — import any Pokédex (regional, fan-made, set-based) as a named JSON file; it appears in the generation filter and the binder reflects its order automatically
- **7 accent themes** — Ghost Purple (default), Ice Blue, Pokémon Blue, Green, Pokéball Red, Pikachu Yellow, Eevee Brown; all work in dark and light mode
- **Light/Dark mode** — toggle in the header, persisted between sessions
- **3 languages** — Português, English, 日本語
- **Keyboard shortcuts** — `Ctrl+F` focus search, `Esc` clear, `↑↓` navigate autocomplete, `←→` navigate binder pages
- **Zero dependencies** — single self-contained HTML file, works offline

---

## 📐 How the slot calculation works

Each binder page holds **S = size² cards** (4, 9 or 16). The default 3×3 grid:

```
1 │ 2 │ 3
──┼───┼──
4 │ 5 │ 6
──┼───┼──
7 │ 8 │ 9
```

Given a Pokédex number `n`:

```
Page = ceil(n / S)
Slot = ((n − 1) mod S) + 1

where S = slots per page (2×2 → 4, 3×3 → 9, 4×4 → 16)
```

Example (3×3): Pikachu (#25) → Page 3, Slot 7 (bottom-left)
Example (2×2): Pikachu (#25) → Page 7, Slot 1 (top-left)

---

## 🚀 Getting started

Download `index.html` and open it in any modern browser. That's it — no server, no install, no build step.

Or visit the live version at: **[Pokémon Binder Locator](https://djandrevilela.github.io/pokemon-binder-locator/)**

---

## 💾 Data & privacy

- All data is stored in your browser's **localStorage only**
- Nothing is ever sent to any server
- Clearing browser cache/history will delete your collection — **export your JSON regularly** (there is no cloud copy)
- The only external requests are Pokémon sprites loaded from PokéAPI's public CDN

---

## 📂 Importing a custom Pokédex

Use the **Import Pokédex** button in the header to load any named Pokédex. After selecting the file, you'll be prompted to give it a name (e.g. "Hoenn Regional", "Set SV01"). It will be saved permanently and appear alongside National and Gen I–IX in the generation filter.

When a custom Pokédex is active, the binder reorders automatically — slot 1 of page 1 becomes the first Pokémon of that Pokédex, regardless of its National Pokédex number.

## 📂 Importing the National Pokédex (for autocomplete)

To improve autocomplete with the full Pokédex (all 1025 Pokémon), import a JSON file in this format:

```json
{
  "pokemon_entries": [
    { "entry_number": 1, "pokemon_species": { "name": "bulbasaur", "url": "..." } },
    { "entry_number": 2, "pokemon_species": { "name": "ivysaur", "url": "..." } }
  ]
}
```

This data is available from the [PokéAPI](https://pokeapi.co/api/v2/pokedex/1/).

---

## ☕ Support

This tool is free and will always be free. If it saves you time hunting through your binder, consider buying me a coffee:

**[ko-fi.com/djandrevilela](https://ko-fi.com/djandrevilela)**

---

## 📄 License

MIT — do whatever you want with it. Attribution appreciated but not required.

---

*Not affiliated with The Pokémon Company, Nintendo, or Game Freak.*
