# 📲 Open-App

**A tiny, generic app launcher via URL parameters (Android-friendly deep-link gateway)**

This repository hosts a lightweight web utility that lets you **open native mobile apps from a standard HTTPS link**.
It works by translating a URL parameter into an app URL scheme (deep link), attempting to launch the app, and gracefully falling back to the Play Store if the app is not installed.

It’s designed for use in:

* 📅 Calendar events (Google Calendar, Outlook, etc.)
* 📧 Emails and messaging apps
* 🌐 Websites and QR codes
* 📄 Documents and wikis

---

## 🚀 Live Demo

```url
https://adrianartacho.github.io/open-app/?app=noom
```

Try changing the `app` parameter:

```url
https://adrianartacho.github.io/open-app/?app=spotify
https://adrianartacho.github.io/open-app/?app=youtube
https://adrianartacho.github.io/open-app/?app=maps
```

---

## 🧠 How It Works

1. You open a normal HTTPS link:

   ```url
   ?app=spotify
   ```

2. The page converts it into a deep link:

   ```url
   spotify://
   ```

3. Android tries to open the corresponding app
4. If the app isn’t installed, the page redirects to a **Play Store search** for that app name

This makes it safe to share links across platforms and contexts.

---

## 🧩 Supported Aliases

Some apps use non-obvious URL schemes. This project includes a small alias map for convenience:

| Parameter  | Opens            |
| ---------- | ---------------- |
| `noom`     | `noom://`        |
| `spotify`  | `spotify://`     |
| `youtube`  | `vnd.youtube://` |
| `whatsapp` | `whatsapp://`    |
| `telegram` | `tg://`          |
| `signal`   | `sgnl://`        |
| `maps`     | `geo://`         |

You can extend this list easily in `index.html`.

---

## 📅 Example Use Cases

### Google Calendar

Put this in an event description:

```url
Open App:
https://adrianartacho.github.io/open-app/?app=noom
```

Tapping the link on Android will open the app directly.

### QR Code

Generate a QR code for:

```url
https://adrianartacho.github.io/open-app/?app=spotify
```

Scan → App opens → Fallback to Play Store if needed.

### Documents / Wikis

Use this as a universal “Open in App” link that works across browsers and messaging platforms.

---

## 🛠️ Customization

### Add a New Alias

Edit this block in `index.html`:

```js
const aliases = {
  noom: "noom",
  spotify: "spotify",
  youtube: "vnd.youtube",
  whatsapp: "whatsapp",
  telegram: "tg",
  signal: "sgnl",
  maps: "geo"
};
```

Add your own:

```js
ableton: "abletonlink"
```

Now:

```url
?app=ableton
```

→ `abletonlink://`

---

## 🔮 Roadmap Ideas

* `&path=` support for deep-linking into app content
  Example:

  ```url
  ?app=spotify&path=track/4uLU6hMCjMI75M1A2tKUQC
  ```

* iOS fallback support (`itunes.apple.com` / `apps.apple.com`)
* Custom fallback URLs (website instead of Play Store)
* Web UI for generating links and QR codes

---

## 🌐 Hosting

This project is designed to run on **GitHub Pages**:

1. Fork or clone this repo
2. Enable Pages (Settings → Pages → Branch: `main` → `/root`)
3. Access your launcher at:

   ```url
   https://<username>.github.io/<repo-name>/
   ```

---

## 📄 License

MIT — use it, fork it, adapt it, and embed it into your own toolchains freely.

---

## 🙌 Credits

Built as a minimal, reusable utility for bridging **web links and native app experiences** in calendar-driven, participatory, and mobile-first workflows.
