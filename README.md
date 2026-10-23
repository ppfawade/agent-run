# Agent Run!!

A fast, kid-friendly vertical-scrolling arcade game for events (ages 8-14). You are a secret agent in a three-piece suit who steals a Quantum Chip and escapes down a tower by smashing through the floors. The whole game is one self-contained HTML file with no dependencies, no build step and no internet needed.

## How to play

| Action | Touch | Keyboard |
| --- | --- | --- |
| Smash the floor | Swipe down, or the Smash button | S or Down arrow |
| Jump | Swipe up, tap, or the Jump button | W, Up arrow or Space |

The agent runs left and right on his own. You choose when to jump and when to smash.

- Only the cracked section of each floor (40% of its width) can be smashed. The rest is steel.
- One smash breaks one floor. Holding the key does nothing extra.
- Collect gold, smash furniture and stomp enemies for points.
- Stomp a robot or the evil dog once to make it dizzy, twice to knock it out.
- Dodge the laser robot's beam, the kicking robot's kick and the charging dog.
- Three guards chase you from the roof and trail you down through the broken floors. Getting hurt lets them gain on you.
- You have 3 hearts and 3 minutes, and each player gets one attempt.

### Scoring

Gold is worth 10 each, smashed furniture 25, a knocked-out enemy 50, a dizzy hit 15 and each new floor 20. Quick chains of pickups build a combo of up to x3.

## Run locally

Open `index.html` in any modern browser (Chrome, Edge, Firefox or Safari). No server is needed. To use a local server instead:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deploy

### GitHub

1. Create a new repository on GitHub.
2. Upload every file in this folder, or push from the command line:

```bash
git init
git add .
git commit -m "Agent Run!!"
git branch -M main
git remote add origin https://github.com/<your-user>/<your-repo>.git
git push -u origin main
```

### Vercel

1. In Vercel choose **Add New, then Project**, and import the repository.
2. Set **Framework Preset** to **Other**. Leave the build command and output directory empty.
3. Click **Deploy**. Every later push to `main` redeploys automatically.

Or with the CLI: `npm i -g vercel`, then run `vercel --prod` in this folder.

## Event notes

- **Scores** are saved in the browser's local storage (key `agentrun_scores_v1`). The start screen lists the 10 most recent games with names, and the game-over screen shows the top 5. Scores are per browser and per device, so use one device if you want a single shared list.
- To reset the scores, clear the site data for the page in the browser settings, or run `localStorage.removeItem('agentrun_scores_v1')` in the browser console.
- **Next Player** on the game-over screen resets the game for the next child.
- Sound effects start after the first tap on Start, as browsers require.
- The deployed Vercel site is public by default. Turn on Deployment Protection in the project settings if you want to restrict it.

## Tuning

Edit these in the script near the top of `index.html`:

- `TIME` is the game length in seconds (default 180).
- `FH` is the height of each floor.
- In `trail()`, the delays `[1,1.7,2.4]` set how far behind the guards run. Smaller numbers make them harder to escape.
- In `mkFloor()`, the spawn chance `.2+d*.5` controls how often enemies appear.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The complete game |
| `vercel.json` | Clean URLs and basic headers for Vercel |
| `.gitignore` | Ignores Vercel and OS files |
| `README.md` | This file |
