# Konnect: First-wash camera guide (D4 prototype)

CS3014 Applied HCI, Team 05. A phone-camera guide for setting up and starting a heavy load on a **Panasonic NA-F135A1** top-load washing machine, one step at a time.

> Read [CONTEXT.md](CONTEXT.md) first if you want to build on this. See [CHANGELOG.md](CHANGELOG.md) for every change.

## Files

| File | What it is |
|---|---|
| `konnect-prototype.html` | The working app (single file: HTML, CSS, JS, no framework, no build) |
| `site/index.html` | Copy of the app for GitHub Pages. **Re-copy after every edit** (see below) |
| `Konnect_D4_PartA_Wireframes.drawio` | Part A wireframes (open at app.diagrams.net) |
| `CONTEXT.md` | Master context: project, decisions, design, how it works, open work |
| `CHANGELOG.md` | Every change, newest first |

## Run on your laptop (webcam)

Browsers only allow the camera on `https://` or `localhost`, **not** when you double-click the file.

```bash
python -m http.server 8765 --bind 127.0.0.1
```

Open `http://127.0.0.1:8765/konnect-prototype.html` in Chrome or Edge, click **First wash**, and allow the camera.

## Run on your phone (needs HTTPS)

### Option A: GitHub Pages (recommended for the demo)

1. Push this repo to GitHub.
2. Repo page → **Settings** → **Pages** (left sidebar, "Code and automation").
3. **Source:** Deploy from a branch. **Branch:** `main`, folder `/ (root)`. Save.
4. Wait about a minute. Open `https://<your-username>.github.io/<repo-name>/site/` on the phone.
5. Allow camera access. It uses the **back camera**.

### Option B: laptop and phone on the same Wi-Fi

Phones refuse the camera on plain `http://` addresses, so the laptop address won't work by itself. Use a tunnel such as `npx localtunnel --port 8765` (or ngrok) to get an `https://` link, and open that on the phone.

### If the camera does not start

- Check the browser's site permissions for camera access (lock icon in the address bar).
- iPhone: use Safari. Android: use Chrome.
- The app shows "Camera is off or blocked". Tap **Show a drawing instead** to use the labelled drawing.

## How to use the app

1. Tap **First wash**.
2. On each step, **tap the real part on the camera view** to place the ring on it (tray, drum, display, control panel). Keyboard: arrow keys to move, Enter to place. Or press **Place ring at the marked spot**.
3. Follow the step. The Next button stays greyed out until the step is done.
4. **Is this normal?** (top right) explains the display number, the lid click and the countdown at any time.
5. **اردو / English** switches the language.

## Facilitator panel (Wizard-of-Oz)

The **Facilitator controls** button at the bottom opens the simulated controls:

| Control | Does |
|---|---|
| Recognised / Not recognised | Forces the part-recognition result |
| Make next check fail | The next ring placement fails, showing the "part not recognised" error |
| Lid click heard | Confirms the lid click on step 6 |
| Force drawing mode | Switches to the drawing without a camera |
| Reset to home | Clears placements and returns home |
| Download session log | Saves the event log as JSON |

## What is real and what is simulated

- **Real:** the camera feed, the overlay, ring placement, all choice and validation logic, the error messages, the "Is this normal?" dialog, English/Urdu, all component states, the event log.
- **Simulated (Wizard-of-Oz):** recognising the part. The app does not detect anything. You tell it where the part is by tapping, and a mock check "confirms" it after 0.7 s. The lid click is confirmed by a timer or by the facilitator.
- **Not tested:** recognition accuracy (out of scope at this fidelity), the Urdu text with a native reader, long-term use.

## After editing the app

`site/index.html` is a copy. Update it and push:

```bash
cp konnect-prototype.html site/index.html
git add -A
git commit -m "Describe your change"
git push
```

Then add a line to [CHANGELOG.md](CHANGELOG.md).

## Privacy

Do not commit the earlier submissions or the report. They contain names and student IDs. `.gitignore` already excludes them.
