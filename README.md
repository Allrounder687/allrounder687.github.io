# IT-Feels Deep-Linking Website
This repository serves as the official landing page for **IT-Feels Music**, and hosts the required `.well-known` verification files to enable Native App Deep-Linking on iOS and Android.

## Setup Instructions
Before you publish this to GitHub Pages, you **MUST** update your Android App Signing SHA-256 Fingerprint.

### Step 1: Update Android SHA-256
1. Go to your Google Play Console.
2. Navigate to **Release > Setup > App integrity**.
3. Under **App signing key certificate**, copy the `SHA-256 certificate fingerprint`.
4. Open `.well-known/assetlinks.json` in this repository.
5. Replace the `XX:XX:XX...` string with your real fingerprint.

*(Note: If you have a separate key for debug builds, you can add a second block to the JSON array with your debug fingerprint).*

### Step 2: Publish to GitHub Pages
1. Go to GitHub.com and create a new public repository (e.g., `allrounder687.github.io`).
2. Push this local folder to your new repository:
   ```bash
   git add .
   git commit -m "Initial commit: Landing page and deep links"
   git branch -M main
   git remote add origin https://github.com/Allrounder687/allrounder687.github.io.git
   git push -u origin main
   ```
3. Once pushed, go to the repository's **Settings > Pages** on GitHub.
4. Under **Build and deployment**, set the Source to **Deploy from a branch**.
5. Select the `main` branch and `/ (root)` folder, and click Save.
6. **Custom Domain:** If you own `itfeelsmusic.app`, enter it in the "Custom domain" section on the Pages settings screen, wait for the DNS check, and enable "Enforce HTTPS".

## How it works
* `index.html`: A beautiful landing page for your app.
* `404.html`: A dynamic router. If a user clicks `itfeelsmusic.app/room/12345` on a desktop, it will use the `itfeelsmusic://` custom scheme to open the Windows app.
* `.well-known/*`: Verification files for Apple (Universal Links) and Google (App Links).
