# pictureperfects.com

Static one-page site for Picture Perfect Photography. No build step, no CMS, nothing to patch. The one outside service is the Instagram widget in the Portfolio section. It is plain HTML that GitHub serves for free.

## Files

| File | What it is |
|---|---|
| `index.html` | The entire site. All styling and scripting is inside this one file. |
| `404.html` | Branded not-found page. |
| `CNAME` | Tells GitHub Pages the custom domain. Do not delete. |
| `assets/` | Logo and icons. |
| `images/` | Your photographs go here. Empty for now. |

## Adding photos later

1. Resize to about 1600px on the long edge, JPEG quality 80. Aim for under 400KB each.
2. Drop the files into `images/`.
3. Open `index.html`, scroll to the bottom, find `const GALLERY = [`.
4. Add one line per photo:

```js
const GALLERY = [
  { src: "images/event-01.jpg", alt: "Sandhi Puja, Durga Puja 2026" },
  { src: "images/headshot-01.jpg", alt: "Corporate headshot" },
];
```

5. Save and commit. The Work section and the nav link appear automatically.
   While the list is empty they stay hidden, so the site never looks unfinished.

Ten to twenty images is the right number. A short, strong set beats a long, uneven one.

## Portfolio section (Instagram)

The Portfolio section shows the [pic.perf.photography](https://www.instagram.com/pic.perf.photography/) Instagram account through a LightWidget embed.

- **Widget:** `e1b7babbd634524a9d07a8dcc75cc9c2`, upgraded (one-time fee, paid). It loads from `cdn.lightwidget.com`
- **Shared:** the same widget also runs the Photography page on [sidsinha.com](https://sidsinha.com), so changes show on both sites
- **Updates:** new Instagram posts appear within about 30 minutes
- **Layout:** columns, photo count and spacing are set in the LightWidget dashboard, not in this code
- **If it goes blank:** the Instagram connection has expired. Reconnect the account in LightWidget. The warning email goes to hi@sidsinha.com

This is separate from the Work gallery below, which uses photos stored in `images/`. Self-hosted photos help local search in a way Instagram photos cannot.

## Deploying

See DEPLOY.md.
