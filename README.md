# Naruto Jutsu 🍥

A browser-based app that uses your webcam, hand tracking, and machine learning to trigger three Naruto jutsu effects in real time.

## Jutsu

| Gesture | Jutsu |
|---|---|
| 🤞 Both hands — cross-finger sign | Shadow Clone |
| 👋 Right hand open | Rasenshuriken |
| 🖐️ Left hand open | Chidori |

## How It Works

- **MediaPipe Holistic** tracks hand landmarks through the webcam
- **MediaPipe Selfie Segmentation** isolates your body from the background
- A **TensorFlow.js neural network** (trained by you) recognizes the Shadow Clone hand sign
- **Open hand detection** using wrist-to-fingertip distance triggers Rasenshuriken and Chidori
- All effects are rendered directly onto an HTML5 **canvas** element in real time

## My Contributions

This project is an extension of two original projects (credited below). Here is what I added and changed:

- Integrated both original projects into a single unified app
- Added **Rasenshuriken** (right hand) and **Chidori** (left hand) jutsu effects
- Implemented open hand detection using MediaPipe landmark distance calculations
- Added smooth fade in/out for jutsu effects using a power value system
- **Canvas-based video rendering** — the original project by gprem09 used CSS positioning to place video elements over the page. In this project, each frame of the jutsu video is drawn directly onto the HTML5 canvas using `ctx.drawImage()` with `globalCompositeOperation: 'screen'` to remove the black background. This approach is more consistent with the rest of the canvas-based rendering pipeline and gives better control over blending and positioning
- Added auto-reset for Shadow Clone after 10 seconds
- Prevented jutsu conflicts — Rasenshuriken and Chidori won't trigger during Shadow Clone
- Cleaned up the UI to a minimal fullscreen experience

## Getting Started

### Prerequisites
- Node.js installed
- A webcam
- Google Chrome (recommended)

### 1. Clone the repo

```bash
git clone https://github.com/Roshini-Botla/naruto-jutsu.git
cd naruto-jutsu
```

### 2. Start the local server

```bash
npx serve -p 3000
```

### 3. Train your gesture model

Navigate to `http://localhost:3000/trainer` in Chrome.

- Record **60+ samples** of your chosen Shadow Clone hand sign
- Record **60+ samples** of other random hand positions
- Click **Train Model**
- Click **Save Model** — this downloads `gesture-model.json` and `gesture-model.weights.bin`
- Place both files in the project root folder

### 4. Run the app

Navigate to `http://localhost:3000` in Chrome, allow camera access, and perform your jutsu! 🔥

## Files

| File | Description |
|---|---|
| `index.html` | Main app |
| `script.js` | All jutsu logic — gesture detection, clone rendering, rasenshuriken, chidori, smoke effects |
| `styles.css` | Minimal fullscreen styling |
| `trainer.html` | UI for recording hand sign samples and training the model |
| `trainer.js` | Training logic and model definition |
| `assets/` | Smoke sprites, jutsu videos, overlay images |

## Tech Stack

- TensorFlow.js
- MediaPipe Holistic
- MediaPipe Selfie Segmentation
- HTML5 Canvas
- Vanilla JavaScript

All dependencies loaded via CDN — no installation required.

## Credits

This project is built on top of two amazing open source projects:

- **[nasha-wanich/naruto-shadow-clone-jutsu](https://github.com/nasha-wanich/naruto-shadow-clone-jutsu)** — Shadow Clone ML gesture detection, selfie segmentation, smoke effects, and the core canvas rendering pipeline
- **[gprem09/naruto](https://github.com/gprem09/naruto)** — Rasenshuriken and Chidori video assets and the original open hand detection concept

Full credit to both original authors. This project would not exist without their work!!