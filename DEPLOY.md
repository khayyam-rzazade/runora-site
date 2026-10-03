# Deploying Runora – Step by Step

No command line needed. Everything below happens in the browser.

---

## PART 1 – Put the files on GitHub

### 1. Create a GitHub account
Go to github.com and sign up, if you do not already have an account.

### 2. Create a repository
- Click the **+** in the top right, then **New repository**
- Repository name: `runora-site`
- Set it to **Public**
- Do **not** tick "Add a README file" – you already have one
- Click **Create repository**

### 3. Upload the files
On the empty repository page, click **uploading an existing file**.

Drag in:
- `index.html`
- `README.md`
- the whole `img` folder

Then click **Commit changes** at the bottom.

You should now see `index.html` and `img` listed in the repository.

---

## PART 2 – Connect Cloudflare to GitHub

### 4. Create the project
In the Cloudflare dashboard:
- Go to **Compute (Workers)**
- Click **Create**
- Choose **Import a repository** (not "Upload assets")
- Connect your GitHub account when prompted and authorise Cloudflare
- Select the `runora-site` repository

### 5. Build settings
When asked for build configuration:
- Framework preset: **None**
- Build command: **leave empty**
- Build output directory: **/** (just a forward slash)

Click **Save and Deploy**.

Wait about a minute. Cloudflare gives you a URL like `runora-site.pages.dev`.
Open it and check the site loads.

---

## PART 3 – Attach runora.az

### 6. Clear the old records first
In Cloudflare, open **runora.az** then **DNS → Records**.
Delete any **A**, **AAAA** or **CNAME** record whose name is `runora.az` or shows as `@`.
Leave anything related to email alone.

### 7. Add the custom domain
Back in the `runora-site` project:
- **Settings → Domains & Routes → Add → Custom domain**
- Enter `runora.az`
- Confirm

Cloudflare creates the DNS record itself. Give it a few minutes for the
certificate to be issued.

### 8. Check it
Open `https://runora.az` in a private window.

If your own wi-fi still shows the old page, that is your network's DNS cache,
not the site. Try mobile data to confirm, or set your DNS to 1.1.1.1.

---

## PART 4 – Making changes later

1. Go to your repository on github.com
2. Click the file you want to change, then the pencil icon
3. Edit, then **Commit changes**
4. Cloudflare rebuilds automatically within about a minute

To add photos: open the `img` folder in the repository, click **Add file →
Upload files**, drag the photos in, commit. They appear on the site
automatically.

---

## If something goes wrong

**Site shows 404** – `index.html` is probably not at the top level of the
repository, or is named something else. It must be exactly `index.html`,
all lowercase, sitting beside the `img` folder.

**Photos do not appear** – check the filename matches exactly, including
lowercase and the `.jpg` extension. `Hero.JPG` will not work; `hero.jpg` will.

**Domain still shows the old page** – DNS cache. Wait, or try mobile data.
