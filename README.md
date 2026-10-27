# Lees Saam – Afrikaanse leesapp

An Afrikaans learn-to-read app for children. There are 20 short stories over 4 levels. The microphone listens as the child reads and each word glows green when read correctly. Tap any word to hear it, or press **Lees die sin** to hear the whole sentence. A parent/teacher view (📊) tracks each child's progress.

## What's in this folder

| File | Purpose |
|---|---|
| `index.html` | The whole app (stories, reader, mic recognition, parent view) |
| `manifest.webmanifest` | Lets the app be installed with "Add to Home Screen" |
| `sw.js` | Service worker that keeps the app opening when offline |
| `icons/` | App icons for phones, tablets and desktops |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

## Put it on GitHub Pages

1. Create a free account at github.com and click **New repository**. Give it a name like `lees-saam` and make it **Public**.
2. Click **uploading an existing file**. Drag in everything from this folder, including the `icons` folder and `.nojekyll`, then click **Commit changes**.
   - `.nojekyll` is a hidden file. If your computer hides it, the app still works without it.
3. Go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, then branch **main**, folder **/ (root)**. Click **Save**.
4. After 1–2 minutes the app is live at
   `https://YOUR-USERNAME.github.io/lees-saam/`

## Install it like an app

- **Android (Chrome):** open the link, tap ⋮ and choose **Add to Home screen / Install app**.
- **Windows/Mac (Chrome or Edge):** click the install icon in the address bar.
- **iPad/iPhone:** Share and **Add to Home Screen**. Note that the mic recognition does not work on iOS. Reading and tap-to-hear do.

## Browsers

| | Mic recognition | Afrikaans voice without Azure |
|---|---|---|
| **Edge** (Windows/Mac) | ✅ | ✅ Adri & Willem built in, free |
| **Chrome** (Windows/Mac) | ✅ | ❌ usually none, so add Azure key or use Edge |
| **Chrome** (Android) | ✅ | ⚠️ depends on the device's text-to-speech voices |
| Safari / Firefox / iOS | ❌ | varies |

Mic recognition needs an internet connection, because the browser sends the audio to Google (Chrome) or Microsoft (Edge).

## Optional: Adri's voice via Azure

1. Create a **Speech** resource in the Azure portal. The free F0 tier gives 500,000 characters a month.
2. Copy **Key 1** and the **Region** (e.g. `southafricanorth`).
3. In the app, open ⚙️, paste the key and region, then press **Toets stem**.

⚠️ **Never put your Azure key into the code or this repository.** Anyone can see a GitHub Pages repo. The key you paste in ⚙️ is stored only in that browser on that device.

## Where progress is saved

Progress is stored in the browser on each device (localStorage). A child reading on a different device starts fresh there. Clearing browser data erases progress, so use **📊 → Laai alle vordering af (CSV)** regularly as a backup.

## Updating the app

Upload a new `index.html` over the old one. If you change files and want to be sure everyone gets the new version immediately, also change `lees-saam-v1` to `lees-saam-v2` in `sw.js`.

## Adding your own stories

Open `index.html` and find `const STORIES = [`. Add a line in the same format:

```js
{id:'uniek-id', level:2, emoji:'🐄', title:'Die koei', sentences:['Die koei is bruin.','Sy eet gras.']},
```

Each `id` must be unique. `level` is 1–4. Use `’n` (with the curly apostrophe) for the indefinite article.
