# GestureDrive

Edge/Chrome extension (Manifest V3). Scroll any page with your index finger and steer browser games
(like an Angular car game) with your thumbs, using your webcam. Everything runs on your device.



<img width="1536" height="1024" alt="0b5cc434-c7f6-4083-b9f0-90d2e27cddec" src="https://github.com/user-attachments/assets/b6a5e36d-1f36-498b-a1ad-ff5576706d8b" />







| Gesture | Action |
|---|---|
| Index finger up, other fingers curled | Scroll (move the finger up or down) |
| Left hand fist, thumb out | Steer left (holds ArrowLeft) |
| Right hand fist, thumb out | Steer right (holds ArrowRight) |

## Install
1. Clone or download this repo.
2. Open `edge://extensions` (or `chrome://extensions`) and turn on **Developer mode**.
3. Click **Load unpacked** and choose the **`extension`** folder (the one containing `manifest.json`).
4. Open your game page (`https://` or `localhost`), click the GestureDrive icon, and press **Start on this tab**
   (or press **Alt+Shift+G**). Allow the camera when asked.

## Settings (popup)

Scroll speed, invert scroll, swap left/right hand, steer with arrow keys, and Fast/Accurate tracking.

## Troubleshooting

- The preview in the page corner shows milliseconds per frame and fps. Under about 30 ms and 25+ fps is healthy.
- Slow? Turn on "Use graphics acceleration when available" and turn off Efficiency mode in `edge://settings/system`.
- Only one camera tracker should run at a time. Remove older gesture extensions.
- Left and right reversed? Untick "Swap left / right hand".
- "Camera blocked": allow the camera from the address bar icon, then press Start again.
- Plain `http://` pages cannot use the camera. Use `https://` or `localhost`.
- Game ignores steering: click inside the game once so it has keyboard focus.

## How it works

- `extension/content.js` adds a small preview frame to the page, scrolls the page, and sends arrow-key events.
- `extension/tracker.*` and `extension/gesture-logic.js` run camera + hand tracking in an isolated extension frame.
- `extension/mediapipe/` is the bundled MediaPipe Hands runtime (Manifest V3 forbids loading code from the internet).



