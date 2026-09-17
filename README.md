# SpendSense — Personal Budgeting & Wealth Tracking

SpendSense is a modern, tactile personal finance and budgeting web application crafted with high contrast, accessible typography, and responsive micro-interactions. It features smart category budgeting, emergency milestones, interactive analytics, and an offline-first architecture.

![SpendSense](public/icon-512.png)

---

## Features

- **Branded Splash Screen**: Polished introductory splash sequence with real-time loading progress.
- **Secure Authentication Screen**: 1-Tap quick login, credential entry, security PIN, and device persistence.
- **Financial Balance & Emergency Runway**: Real-time spending health status, burn-rate calculation, and liquid savings metrics.
- **Category-Level Budgets**: Dynamic category allocation with interactive progress bars, remaining allowances, and overspend warnings.
- **Interactive Analytics**: Monthly and weekly breakdown charts, expense distribution, and savings rate benchmarking.
- **Savings Vaults & Milestone Tracker**: Goal-oriented savings envelopes with deposit actions and visual milestone completion indicators.
- **Transaction Ledger**: Filter, search, and export transactions to CSV.
- **Progressive Web App (PWA) Ready**: Web App Manifest (`manifest.webmanifest`), mobile service worker, high-resolution app icons, and standalone mobile display mode.

---

## Tech Stack

- **Framework**: React 19 + TypeScript + Vite 6
- **Styling**: Tailwind CSS 4 (modern engine)
- **Icons**: Lucide React
- **Animations**: Motion (`motion/react`)
- **Persistence**: Encrypted/Structured Local Storage (Offline-First)

---

## Getting Started Locally

### Prerequisites

- Node.js (v18 or higher recommended)
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/<YOUR_USERNAME>/<YOUR_REPOSITORY>.git
cd spendsense

# Install dependencies
npm install

# Start the local development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to test the application.

### Production Build

```bash
# Type check and build static production bundle into dist/
npm run build

# Preview production build locally
npm run preview
```

---

## Pushing This Project to GitHub

### Option A: Using Google AI Studio (Easiest — 1 Click)

1. In the Google AI Studio top-right corner, click on the **Export** / **Settings** menu (three dots or share button).
2. Select **"Export to GitHub"** (or **"Push to GitHub"**).
3. Connect your GitHub account and authorize AI Studio.
4. Select a repository name (e.g., `spendsense`) and click **Confirm Export**. Your complete codebase will be created in your GitHub account instantly.

### Option B: Using Git Command Line

If you have downloaded the ZIP or are working in a terminal:

```bash
# 1. Initialize git if not already done
git init
git add .
git commit -m "feat: initial commit of SpendSense budgeting app"

# 2. Rename branch to main
git branch -M main

# 3. Create a new repository on https://github.com/new (do NOT check 'Initialize with README')
# 4. Link your local repo to GitHub:
git remote add origin https://github.com/<YOUR_USERNAME>/<YOUR_REPO_NAME>.git

# 5. Push code to GitHub
git push -u origin main
```

---

## Publishing to Google Play Store

Because SpendSense is already built as a Progressive Web App (PWA) with a valid `manifest.webmanifest` and responsive mobile layouts, you can easily package it into an **Android App Bundle (.aab)** for the Google Play Store using **Google's Official Bubblewrap CLI (Trusted Web Activity - TWA)** or **Capacitor**.

### Method 1: Google Bubblewrap CLI (Official Google TWA Method)

Google's Bubblewrap CLI takes your deployed web app and wraps it into a verified Android app running in Chrome's native engine.

1. **Deploy your app to production** (e.g., Vercel, Netlify, Cloud Run, or GitHub Pages) to get a public HTTPS URL (such as `https://spendsense.app`).
2. **Install Bubblewrap globally**:
   ```bash
   npm install -g @bubblewrap/cli
   ```
3. **Initialize the Android Project**:
   ```bash
   bubblewrap init --manifest https://spendsense.app/manifest.webmanifest
   ```
   Follow the interactive prompts:
   - App Name: `SpendSense`
   - Package ID: `com.spendsense.app`
   - Display Mode: `standalone`
   - Icon URL: `https://spendsense.app/icon-512.png`
   - Generate signing keystore: Yes (Save your `key.keystore` safely!)
4. **Build Android App Bundle (.aab)**:
   ```bash
   bubblewrap build
   ```
5. You will get an `app-release-bundle.aab` file ready to upload to the **Google Play Console**!

---

### Method 2: Capacitor (Native Android Studio Wrapper)

If you prefer building directly with Android Studio and Gradle:

1. **Install Capacitor**:
   ```bash
   npm install @capacitor/core @capacitor/cli @capacitor/android
   npx cap init SpendSense com.spendsense.app --web-dir dist
   ```
2. **Build the web assets**:
   ```bash
   npm run build
   ```
3. **Add Android platform**:
   ```bash
   npx cap add android
   npx cap sync
   ```
4. **Open in Android Studio**:
   ```bash
   npx cap open android
   ```
5. In Android Studio, go to **Build > Generate Signed Bundle / APK > Android App Bundle (.aab)**.
6. Create your signing key and generate the signed `.aab`.

---

### Uploading to Google Play Console

1. Create or log in to your [Google Play Console](https://play.google.com/console) developer account.
2. Click **Create App** → Set App name to **SpendSense**, category to **Finance**, Free/Paid.
3. Fill out the Store Listing (Screenshots, Short Description, App Icon).
4. Go to **Production** or **Internal Testing** → **Create new release**.
5. Upload your signed `.aab` file generated above.
6. Set up Digital Asset Links (`assetlinks.json`) if using TWA so the URL address bar is hidden.
7. Submit for review!

---

## License

MIT License. Designed with care for clean, accessible financial tracking.
