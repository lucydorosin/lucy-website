# Publishing lucydorosin.com and giving Lucy her own editor

This folder is the whole website. It's built so that Lucy can log in at
`lucydorosin.com/admin` and edit the text, photo, and scripts herself —
no code, no asking you for help — while you (or nobody) never has to touch
the HTML again.

Do these steps once. After that, publishing an edit is just Lucy clicking
"Publish" inside the editor.

## What you're setting up, in plain terms

- **GitHub** — free storage for the website's files (like a Google Drive
  for code). This is the thing Netlify watches for changes.
- **Netlify** — free hosting that takes the files from GitHub and serves
  them as the live website, and auto-updates every time something changes.
- **Netlify Identity + Git Gateway** — this is what lets Lucy log in with
  just an email/password (no GitHub account needed) and have her edits
  saved automatically.
- **Decap CMS** — the actual editor Lucy sees. It's already built into
  this folder (`/admin`), pre-configured with simple forms for each
  section of the site (Home, Writing, Films, Contact).

## Step 1 — Register the domain

You said lucydorosin.com still needs to be registered. Any registrar
works; two easy options:

1. Go to **namecheap.com** or **cloudflare.com/products/registrar**
2. Search `lucydorosin.com`
3. Buy it (roughly $12–20/year — Cloudflare tends to be the cheapest,
   at close to wholesale cost)

You don't need any hosting add-ons they try to upsell — just the bare
domain. Keep the login for whichever registrar you use; you'll come back
in Step 5 to point the domain at Netlify.

## Step 2 — Put these files on GitHub

1. Create a free account at **github.com** if you don't have one.
2. Click **New repository**. Name it something like `lucy-website`.
   Keep it private or public, doesn't matter.
3. Upload every file and folder in this delivered folder into that
   repository (GitHub's web uploader lets you drag-and-drop a whole
   folder — look for "uploading an existing file" on the repo's page).
   Make sure the folder structure stays intact: `index.html`, `data/`,
   `assets/`, `admin/`, and `netlify.toml` should all sit at the top
   level of the repo, not nested inside another folder.

## Step 3 — Connect Netlify

1. Create a free account at **netlify.com** (you can sign up directly
   with your GitHub account — makes this step faster).
2. Click **Add new site → Import an existing project**, choose GitHub,
   and pick the `lucy-website` repo.
3. Leave the build settings blank/default (there's no build step — it's
   a static site) and click **Deploy**.
4. Netlify gives you a random URL like `chic-lovelace-123abc.netlify.app`.
   Open it and confirm the site loads correctly.

## Step 4 — Turn on Identity + Git Gateway (this is what makes /admin work)

1. In your new Netlify site's dashboard, go to **Site configuration →
   Identity** and click **Enable Identity**.
2. Still under Identity settings, find **Registration** and set it to
   **Invite only** (so random people online can't sign themselves up as
   editors).
3. Go to **Site configuration → Identity → Services → Git Gateway** and
   click **Enable Git Gateway**. This is the piece that lets Netlify
   Identity users (like Lucy) save changes back to GitHub without
   needing their own GitHub account.

## Step 5 — Point the domain at Netlify

1. In Netlify: **Site configuration → Domain management → Add a domain**,
   enter `lucydorosin.com`.
2. Netlify will show you DNS records to add (usually just changing the
   domain's nameservers to Netlify's, which is the simplest option it
   offers).
3. Go back to wherever you registered the domain (Step 1) and update the
   nameservers (or the specific records Netlify shows you) accordingly.
4. DNS changes can take anywhere from a few minutes to a few hours to
   take effect. Netlify will also auto-provision a free HTTPS certificate
   once the domain is pointed correctly, so the site loads securely.

## Step 6 — Invite Lucy

1. In Netlify: **Site configuration → Identity**, click **Invite users**,
   and enter Lucy's email address.
2. She'll get an email with a link to set her own password.
3. From then on, she edits by going to **lucydorosin.com/admin**, logging
   in with that email/password, and using the editor.

## What Lucy can do herself, going forward

Once logged in at `/admin` she'll see four simple sections to edit:

- **Home Page** — the intro text/eyebrow line, her bio (just leave a
  blank line between paragraphs), the photo, and the three "facts"
  (Based in / Focus / Currently).
- **Writing Section** — add, remove, or reorder script entries; each one
  has a title, a tag line, a blurb, and an optional PDF upload (drag a
  new script PDF right into the field — no file naming or emailing
  required).
- **Films Section** — same idea for the films; there's a "Video embed
  URL" field on each film that's blank right now. Once a film is hosted
  on Vimeo (see the video-hosting notes from earlier in this project),
  paste its **embed** URL there (looks like
  `https://player.vimeo.com/video/123456789`) and the placeholder
  thumbnail on the live site automatically turns into the real playable
  video — no other changes needed.
- **Contact Section** — email address and social links.

Every change has a **Publish** button. Clicking it commits the change to
GitHub, which Netlify picks up automatically and the live site updates
within a minute or two — no code, no re-uploading files, no waiting on
you.

## If something ever needs a real code change

Anything structural — new sections, a different layout, new fonts, a
different color scheme — still requires editing `index.html` directly
rather than the CMS forms (the CMS only edits content, not design). For
that, come back here and I can make the change and walk you through
re-uploading it to GitHub (or just tell me to do it and hand me updated
files).
