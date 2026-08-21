# Deploying pictureperfects.com on GitHub Pages

Free, permanent, and nothing to maintain. Roughly 15 minutes of work, then up to
24 hours of waiting for DNS and the HTTPS certificate.

---

## Step 1. Create the repository

1. Go to https://github.com/new
2. Repository name: `pictureperfects` (any name works)
3. Set it to **Public**. Private repos need a paid plan for Pages.
4. Do **not** add a README, .gitignore or licence. Leave it empty.
5. Click **Create repository**.

## Step 2. Upload the files

On the empty repo page, click **uploading an existing file**.

Drag in everything from this folder:

```
index.html
404.html
CNAME
README.md
DEPLOY.md
assets/          (the whole folder)
images/          (the whole folder)
```

Scroll down, click **Commit changes**.

> Dragging a folder in the browser uploads its contents and keeps the structure.
> If `assets/` does not come through, upload the four files inside it and put them
> in a folder called `assets` using **Add file → Create new file** and typing
> `assets/logo.png` as the path.

## Step 3. Turn on Pages

1. In the repo, go to **Settings → Pages**
2. Under **Build and deployment**, Source: **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)**. Click **Save**.
4. Wait about a minute. A green banner gives you a `.github.io` URL. Open it and
   check the site works before touching DNS.

## Step 4. Point the domain at GitHub

In **Settings → Pages → Custom domain**, type `pictureperfects.com` and Save.

Then at your domain registrar, open the DNS settings and create these records.

**Four A records** (Host/Name `@`, or blank, depending on the registrar):

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

**Four AAAA records** (optional but recommended, adds IPv6):

| Type | Name | Value |
|---|---|---|
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |

**One CNAME** for the www version:

| Type | Name | Value |
|---|---|---|
| CNAME | www | `YOUR-GITHUB-USERNAME.github.io` |

Replace `YOUR-GITHUB-USERNAME` with your actual username. The trailing dot is fine
if your registrar adds one.

**Delete any old A, AAAA, CNAME or parking records for `@` and `www`** left over
from the previous host. Leave MX records alone or you will break your email.

## Step 5. Turn on HTTPS

Come back to **Settings → Pages** after DNS propagates. Once GitHub shows the domain
as verified, tick **Enforce HTTPS**. The certificate can take up to 24 hours to issue.
Until then the site works on http and the padlock is missing. That is normal.

---

## Checking it worked

From a terminal:

```
dig pictureperfects.com +short          # should list the four 185.199.x.153 addresses
dig www.pictureperfects.com +short      # should show your username.github.io
```

Not sure who your registrar is:

```
whois pictureperfects.com | grep -i registrar
```

---

## Making changes later

Edit the file on github.com (pencil icon), commit, and the site rebuilds in about a
minute. There is no build to run and nothing to keep updated.

## If you would rather not use GitHub Pages

Cloudflare Pages and Netlify are both free, both accept a drag-and-drop of this same
folder, and both handle HTTPS automatically. GitHub Pages is recommended here only
because you already have an account.
