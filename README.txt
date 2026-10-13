JESA VISION HUD — Prototype 01

REQUIREMENTS
- Laptop with webcam
- Modern Chrome or Edge
- Internet connection for the MediaPipe JS/WASM and hand-landmarker model on first load

RUN (Windows PowerShell)
1. Extract the ZIP.
2. Open PowerShell in the jesa-vision-hud folder.
3. Run: py -m http.server 8000
   If py is unavailable, try: python -m http.server 8000
4. Open: http://localhost:8000
5. Click INITIALIZE CAMERA and allow camera permission.
6. Put one hand in view, palm facing camera, with decent lighting.

GESTURES (heuristic prototype)
- Open palm: sets HUD mode to ACTIVE
- Fist: sets HUD mode to STANDBY
- Pinch: confirms a select-ready event
- Index up: confirms a navigation-ready event
Hold the gesture for about 650 ms. Gesture classification is a lightweight heuristic, not a trained classifier; camera angle and lighting affect results.

CHECKPOINTS
A. Page opens: HUD panels are visible.
B. Camera permission: live webcam appears.
C. Model loads: TRACKING changes to SEARCHING.
D. Hand enters frame: HANDS becomes 1 DETECTED and orange landmarks appear.
E. Hold a gesture: GESTURE and SYSTEM EVENT update.

TROUBLESHOOTING
- Camera error: close other apps using webcam, allow camera permission, reload localhost.
- Model does not load: check internet, then reload. CDN/model download is required.
- Black video: select the correct webcam in browser/OS settings and check camera privacy permissions.
- GPU delegate error: some systems do not support the delegate. In index.html, change delegate:'GPU' to delegate:'CPU'.
- Overlay alignment may vary with unusual camera aspect ratios; this is a prototype.

PRIVACY
Video processing runs in the browser using MediaPipe. This app does not upload frames to a JESA backend. It loads library/model files from public CDNs and Google storage. Do not use for safety-critical decisions.

SCOPE
This is standalone and does not connect to JESA Brain yet. Verify camera and gestures first, then integrate through a deliberate API contract.
