# Preview Screenshots — Attribution

Static screenshots of public homepages used for editorial reference. Trademarks remain with their respective owners. This catalog claims no affiliation with any of the brands shown.

## Captured

| File | Source URL | Brand owner | Date captured |
|---|---|---|---|
| `linear.jpg` | https://linear.app | Linear | 2026-04-22 |
| `ollama.jpg` | https://ollama.com | Ollama | 2026-04-22 |
| `anthropic.jpg` | https://www.anthropic.com | Anthropic PBC | 2026-04-22 |
| `clickhouse.jpg` | https://clickhouse.com | ClickHouse, Inc. | 2026-04-22 |
| `runwayml.jpg` | https://runwayml.com | Runway AI, Inc. | 2026-04-22 |
| `figma.jpg` | https://www.figma.com | Figma, Inc. | 2026-04-22 |
| `arc.jpg` | https://arc.net | The Browser Company | 2026-04-22 |
| `theverge.jpg` | https://www.theverge.com | Vox Media | 2026-04-22 |
| `granola.jpg` | https://www.granola.ai | Granola Labs | 2026-04-22 |

## Capture method

Captured via the [Microlink](https://microlink.io/) screenshot API at viewport `1280x800`, downscaled to `1280px` wide, JPEG quality 75. Files committed to the repo so the README renders without third-party dependency at view-time.

## Refresh policy

Re-capture when:
- A brand visibly redesigns (visit triggers a "this looks different" moment)
- The DESIGN.md file in this repo gets a token update
- The captured page returns a 404 or has clearly broken layout

To re-capture a single brand:

```bash
cd assets/previews
curl -sL -o linear.png "https://api.microlink.io/?url=https://linear.app&screenshot=true&meta=false&embed=screenshot.url&viewport.width=1280&viewport.height=800"
sips -Z 1280 -s format jpeg -s formatOptions 75 linear.png --out linear.jpg
rm linear.png
```

To re-capture the whole gallery: see the loop in commit `add: visual preview gallery` for the batch command.

## Removal requests

If you are the brand owner and prefer not to have your homepage represented here, open an issue or PR removing the corresponding row from the README gallery and the file from this folder. We will action within 48h.

## Why screenshots, not logos

Logos are owned marks; using them implies endorsement. Public-homepage screenshots used as editorial reference are common practice in awesome-list catalogs and design publications. We name the brand, link to the live site, and disclaim affiliation.
