# CSBC PWA — Setup Guide

## What This Is
A Progressive Web App (PWA) shell that wraps your SquareSpace website (csbcroanoke.com). When you update your SquareSpace site, the app automatically shows the latest content since it loads your live site.

## How to Deploy

### Option A: GitHub Pages (Free)
1. Create a GitHub account (if you don't have one) at github.com
2. Create a new repository called `csbc-app`
3. Upload all files from this `csbc-pwa` folder to the repo
4. Go to Settings → Pages → set Source to "main" branch
5. Your app will be live at `https://yourusername.github.io/csbc-app`

### Option B: Netlify (Free)
1. Go to netlify.com and sign up
2. Drag and drop the `csbc-pwa` folder onto the Netlify dashboard
3. Done — you'll get a URL like `https://random-name.netlify.app`
4. You can set a custom domain like `app.csbcroanoke.com`

### Option C: Cloudflare Pages (Free)
1. Go to pages.cloudflare.com
2. Connect your GitHub repo or upload directly
3. Set a custom domain if desired

## How People Install It

### On iPhone/iPad
1. Open the app URL in Safari
2. Tap the Share button (square with arrow)
3. Tap "Add to Home Screen"
4. The app icon appears on their home screen

### On Android
1. Open the app URL in Chrome
2. Chrome will show an "Add to Home Screen" banner automatically
3. Or tap the three-dot menu → "Install app"

### On Desktop (Chrome/Edge)
1. Open the app URL
2. Click the install icon in the address bar
3. The app opens in its own window

## Push Notifications Setup

The app is pre-wired for push notifications. To send them, you need a push service:

### Using OneSignal (Recommended — Free Tier)
1. Create an account at onesignal.com
2. Create a new app, select "Web Push"
3. Enter your app's URL
4. OneSignal will give you a `OneSignal SDK` script and app ID
5. Add the OneSignal script to `index.html` in the `<head>`
6. Replace the push subscription code in `sw.js` with OneSignal's worker
7. Use the OneSignal dashboard to compose and send notifications

### Using Firebase Cloud Messaging (Alternative)
1. Create a Firebase project at console.firebase.google.com
2. Go to Project Settings → Cloud Messaging
3. Generate a VAPID key pair
4. Add the VAPID public key to the push subscription in `index.html`
5. Use the Firebase console or Admin SDK to send notifications

## Customization

### Change Colors
Edit the CSS variables at the top of `index.html`:
- `--accent`: Gold accent color (currently #c9a84c)
- `--bg-primary`: Dark background (currently #1b1b1b)

### Replace Icons
Replace the PNG files in the `icons/` folder with your church logo. Keep the same filenames and sizes. For best results, use a square image with transparent background.

### Update Navigation
Edit the nav items in `index.html`. The bottom tab bar has 5 slots. The slide-out menu has the full navigation tree.

## Custom Domain Setup
For the best experience, set up a subdomain like `app.csbcroanoke.com`:
1. In your domain registrar, add a CNAME record pointing to your hosting provider
2. Configure the custom domain in your hosting dashboard (GitHub Pages, Netlify, etc.)
3. HTTPS will be auto-provisioned

## File Structure
```
csbc-pwa/
├── index.html        # Main app shell with navigation
├── manifest.json     # PWA manifest (name, icons, theme)
├── sw.js             # Service worker (offline + push)
├── offline.html      # Offline fallback page
├── SETUP.md          # This file
└── icons/
    ├── icon-72.png
    ├── icon-96.png
    ├── icon-128.png
    ├── icon-144.png
    ├── icon-152.png
    ├── icon-192.png
    ├── icon-384.png
    └── icon-512.png
```
