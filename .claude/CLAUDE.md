# Weather Site Builder

This repository contains an auto-updating static weather website for San Diego, CA (zip code 92101).

## What this agent does on each run

1. Fetch current weather from the wttr.in API for zip code 92101:
   ```
   curl -s "https://wttr.in/92101?format=j1"
   ```
2. Parse the JSON response to extract current conditions.
3. Generate/overwrite `index.html` at the repo root with all weather data hardcoded into the HTML.
4. Commit and push back to the repository.

## Site requirements

- Single `index.html` file, fully self-contained (inline CSS only, no external runtime dependencies)
- Displays:
  - Location: "San Diego, CA · 92101"
  - Temperature in °F (with °C in parentheses)
  - Weather condition description with an appropriate emoji (☀️ 🌤 ⛅ 🌧 🌩 🌨 etc.)
  - Stat cards: Feels Like, Humidity, Wind speed/direction, UV Index
  - "Last updated" timestamp in UTC, hardcoded at build time
- Clean, modern design using system fonts

## Git push instructions

```bash
git config user.email "weather-bot@claude-tasks"
git config user.name "Claude Weather Bot"
git add -A
git commit -m "chore: update weather $(date -u '+%Y-%m-%d %H:%M UTC')"
git push origin HEAD
```

If the push is rejected because the branch is behind, run `git pull --rebase origin HEAD` first, then push again.
