# ZenTube ⚡📱

**ZenTube** is a lightning-fast, stutter-free, zero-flash Progressive Web App (PWA) built specifically for iOS and mobile browsers. It connects directly to self-hosted Invidious API instances to deliver a clean, privacy-focused YouTube streaming experience with hardware-accelerated playback and native background audio integration.

---

## 🌟 Key Features

* **Stutter-Free & Flash-Free ABR:** Employs a dual-element ping-pong video architecture and pre-roll native audio buffering to eliminate quality-switch flashes and playback hiccups.
* **Native iOS Lock Screen & Control Center Integration:** Fully integrated with `navigator.mediaSession`, supporting 10-second skip buttons, live scrubbing, and hardware lock-screen controls.
* **True PWA Experience:** Designed to run seamlessly in standalone mode (`apple-mobile-web-app-capable`) with dynamic safe-area-inset padding and immersive GPU fullscreen toggles.
* **Subscriptions & Channel Feed:** Connect your Google account to sync live subscription feeds and browse channel upload playlists.
* **Fully Self-Hostable:** Pair it with your own private Invidious proxy instance for complete data privacy and zero ads.

---

## ⚙️ How It Works

ZenTube decouples audio and video streams using direct adaptive format streams fetched dynamically from your configured Invidious API instance:
1. **Audio Engine (`<audio>` element):** Serves as the master clock anchored to the Web Audio API graph, ensuring uninterrupted background playback and persistent lock-screen audio control.
2. **Video Engine (Dual `<video>` elements):** Employs an active/staged ping-pong swapping buffer to handle seamless, zero-flash quality handoffs (e.g., upgrading from 360p to 720p mid-stream without buffering stalls).

---

## 🚀 Getting Started

### Prerequisites
* A modern mobile browser (Safari on iOS or Chrome on Android).
* A running **Invidious API Instance** (publicly available or self-hosted behind an HTTPS proxy).
* A **Google Cloud Console Account** (required if you wish to sync your personal YouTube subscriptions).

---

## 🔑 How to Obtain a Google OAuth Client ID

To sync your personal YouTube subscriptions, ZenTube uses a secure "Bring Your Own Client ID" model. Because ZenTube runs entirely client-side in your browser, you will need to generate your own free OAuth Client ID from the Google Cloud Console. 

Follow these step-by-step instructions:

### Step 1: Create a Google Cloud Project
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Click the project dropdown menu at the top of the page and select **New Project**.
3. Enter a project name (e.g., `ZenTube PWA`) and click **Create**.

### Step 2: Enable the YouTube Data API v3
1. In your newly created project dashboard, navigate to **APIs & Services** > **Library** from the left-hand menu.
2. Type `YouTube Data API v3` into the search bar.
3. Click on the result and press **Enable**.

### Step 3: Configure the OAuth Consent Screen
1. Go to **APIs & Services** > **OAuth consent screen**.
2. Select **External** (or Internal if you are using Google Workspace) and click **Create**.
3. Fill in the required app information:
   * **App name:** `ZenTube`
   * **User support email:** *Your email address*
   * **Developer contact information:** *Your email address*
4. Click **Save and Continue**.
5. On the **Scopes** page, click **Add or Remove Scopes**, search for or select `https://www.googleapis.com/auth/youtube.readonly`, and click **Update**, then **Save and Continue**.
6. Under **Test users**, add your own Google account email address so you can log in during testing. Click **Save and Continue** and return to the dashboard.

### Step 4: Create OAuth Client Credentials
1. Navigate to **APIs & Services** > **Credentials**.
2. Click **+ Create Credentials** at the top of the page and select **OAuth client ID**.
3. Set the **Application type** to **Web application**.
4. Give your client a name (e.g., `ZenTube Web Client`).
5. Under **Authorized JavaScript origins**, click **Add URI** and enter the exact URL where you are hosting ZenTube (e.g., `https://your-username.github.io` or `http://localhost:8080`).
6. Click **Create**.
7. A modal will appear displaying your **Client ID**. 

---

## 📱 Configuring ZenTube

1. Open **ZenTube** in your browser or PWA container.
2. Tap the **Settings** tab in the bottom navigation bar.
3. Paste your **Custom Stream Proxy URL** (your Invidious instance URL, e.g., `https://invidious.example.com`) and click **Save Proxy URL**.
4. Paste your newly generated **Google OAuth Client ID** into the OAuth field and click **Save Client ID**.
5. Head back to the main feed, click **Sign In**, and enjoy your ad-free, stutter-free streaming experience!

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome! Feel free to open an issue or submit a pull request on GitHub.

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

