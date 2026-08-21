# pictureperfects.com

Static one-page site for Picture Perfect Photography. No build step, no dependencies,
no CMS, nothing to patch. It is plain HTML that GitHub serves for free.

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

## Deploying

See DEPLOY.md.
