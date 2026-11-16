# ahmed's site: how to publish and edit

The whole site is one file: `index.html`. There's no build step, framework, or server.
`resume.pdf` sits next to it so the "resume.pdf" button works.

---

## 1. Buy the domain (~10 min, ~$10–15/yr for a .com)

Use **Cloudflare Registrar** (sells at cost, no markup) or **Porkbun** (cheap, simple UI).
Names worth checking: `ahmedelbanna.com`, `elbanna.co`, `ahmedelbanna.design`, `akmtote.com`.
Skip any "hosting", "email" or "site builder" add-ons. You only need the domain.

## 2. Put the site on GitHub (~5 min, free)

1. Make an account at github.com.
2. Click **+ → New repository**. Name it `website`, set it to **Public**, and click Create.
3. On the repo page, click **uploading an existing file**. Drag in `index.html` and `resume.pdf`, then click **Commit changes**.

## 3. Turn on GitHub Pages (~2 min)

1. Open the repo's **Settings → Pages**.
2. Under "Build and deployment", set **Source = Deploy from a branch**, **Branch = main**, folder **/ (root)**, and click Save.
3. Wait about a minute. The site goes live at `https://YOUR-USERNAME.github.io/website/`.

## 4. Connect your domain (~10 min + DNS wait)

1. Still in **Settings → Pages**, under **Custom domain**, type `yourdomain.com` and click Save.
2. At your registrar (Cloudflare/Porkbun), open DNS settings and add these records:

| Type  | Name / Host | Value                     |
|-------|-------------|---------------------------|
| A     | @           | 185.199.108.153           |
| A     | @           | 185.199.109.153           |
| A     | @           | 185.199.110.153           |
| A     | @           | 185.199.111.153           |
| CNAME | www         | YOUR-USERNAME.github.io   |

   On Cloudflare, set each record to **DNS only** (grey cloud), not proxied.
3. Back in GitHub Pages settings, tick **Enforce HTTPS** once it's clickable. That can take anywhere from a few minutes to a few hours.
4. DNS changes can take up to 24h to spread, but they usually land within an hour.

## 5. Updating the site later (~1 min)

On github.com, open `index.html`, click the ✏️ pencil, edit, and **Commit changes**. The site updates about a minute later.
To swap the resume, upload a new `resume.pdf` with the same name.

---

## What to edit in `index.html`

All the content is in the `<script>` block near the bottom, in plain lists:

- `INTRO` / `REPLIES`: the texting thread and the reply buttons
- `MARQUEE`: the scrolling "now" ticker
- `LOG`: work experience rows
- `TOOLKIT`: skills tags
- `PORTFOLIO`: the three tabs of project cards

**Adding photos to a portfolio card:** make an `images` folder in the repo, upload e.g. `bfr.jpg`,
then set `img: "images/bfr.jpg"` on that card. The photo replaces the pixel-art thumbnail.
Landscape images around 1600×1000 look best.

**Links:** any link with an empty `href: ""` is hidden, so filling in Rounds' demo/GitHub URLs makes those buttons appear.

Colors are at the top of the `<style>` block (`--accent` is the blue).
