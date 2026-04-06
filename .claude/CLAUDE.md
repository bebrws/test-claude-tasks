# Weather Site Builder

This repository contains an auto-updating static weather website for San Diego, CA (zip code 92101) and also uses the Github MCP to show a summary of the last commit, not under any Github organaization, but in my personal repositories (user https://github.com/bebrws/).

## What this agent does on each run

1. Fetch current weather from the wttr.in API for zip code 92101:
   ```
   curl -s "https://wttr.in/92101?format=j1"
   ```
2. Parse the JSON response to extract current conditions.
3. Use the Github MCP to get the last commit  summary to my personal repositories. The repository that the summary is generated from should not be this repository.
4. Generate/overwrite `index.html` at the repo root with all weather data hardcoded into the HTML.
5. Commit and push back to the repository.

## Site requirements

- Single `index.html` file, fully self-contained (inline CSS only, no external runtime dependencies)
- Displays:
  - Location: "San Diego, CA · 92101"
  - Temperature in °F (with °C in parentheses)
  - Weather condition description with an appropriate emoji (☀️ 🌤 ⛅ 🌧 🌩 🌨 etc.)
  - Stat cards: Feels Like, Humidity, Wind speed/direction, UV Index
  - "Last updated" timestamp in UTC, hardcoded at build time
  - Last Github commit summary card
- Clean, modern design using system fonts

## Git push instructions

```bash
git config user.email "bradebarrowsdev@gmail.com"
git config user.name "Brad Barrows"
git add -A
git commit -m "chore: update weather $(date -u '+%Y-%m-%d %H:%M UTC')"
git push origin HEAD
```

If the push is rejected because the branch is behind, run `git pull --rebase origin HEAD` first, then push again.
