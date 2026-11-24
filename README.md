<p align="center"><img src="logo.svg" width="96" alt="Thrivemap logo"></p>

<h1 align="center">Thrivemap</h1>

<p align="center">The world ranked by human development: 193 countries and territories, one interactive page.</p>

---

Thrivemap ranks every country in the UN **Human Development Index (HDI)**, the measure that combines life expectancy, years of schooling and income per person on a 0 to 1 scale.

## Features

- **Ranking list**: search, filter by development tier or continent, sort high to low, low to high or A to Z.
- **Interactive world map**: countries coloured by tier, hover for rank and value, click for details, zoom and pan (buttons, double-click, pinch or Ctrl + scroll). Very small states are shown as dots so they stay clickable.
- **Distribution strip**: all 193 countries plotted on the HDI scale, grouped by tier.
- **Country card**: rank, share of countries it outscores, gap to number one, continental rank and average, nearest neighbours in the ranking.
- **Continental averages**, a **Copy list** button (tab-separated, pastes into any spreadsheet) and light and dark themes.

No build step, no framework and no tracking: one HTML file plus a map file. Filters are remembered in the browser's local storage only.

## Run it

Serve the folder with any static server (the map is loaded with `fetch`, so opening the file directly may not show it):

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

It also works as-is on GitHub Pages.

## Data

| What | Source |
| --- | --- |
| HDI values and ranks | UNDP, [Human Development Report 2025](https://hdr.undp.org/data-center/human-development-index) (values for 2023) |
| Tiers | UNDP thresholds: very high ≥ 0.800, high 0.700–0.799, medium 0.550–0.699, low < 0.550 |
| Country borders | [Natural Earth](https://www.naturalearthdata.com/) 1:50m via [world-atlas](https://github.com/topojson/world-atlas), simplified |
| Continents | Grouping added for this project, not a UNDP classification |

Territories without an HDI value (Greenland, Taiwan, Kosovo, Western Sahara and others) are shown in grey. Border depictions do not imply any position on disputed territories.

## Rebuilding the map

`map.json` holds pre-projected country outlines (Natural Earth projection, 1000 px wide). To regenerate it after changing the country list:

```bash
cd tools
npm install
npm run build-map
```

## Files

```
index.html        the app (data, styles and script in one file)
map.json          projected country outlines
logo.svg          logo
tools/            script that builds map.json
```

## License

Code under the [MIT License](LICENSE). HDI data © UNDP; Natural Earth data is public domain.
