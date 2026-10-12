# ARVIND — Research & Industry Portfolio

A responsive, no-build, GitHub Pages portfolio with a visual content editor. All public content lives in `data/content.json`.

## Features

- Responsive research website, interactive tabs, publication filters and timeline
- Dark/light mode, smooth section navigation and reading progress indicator
- Sections: profile, career, education, publications, projects, certifications, patents, copyrights, achievements, talks, and service
- Browser-based editor at `/admin.html`: create, edit, reorder, delete, import and export entries
- Commit edits through the official GitHub Contents API using a fine-grained personal access token
- Semantic HTML and mobile-friendly layouts
- No npm packages, database, paid hosting, build process, or backend required

## Fast setup: `USERNAME.github.io`

1. Sign in at [github.com](https://github.com/).
2. Create a **public** repository whose name is exactly `USERNAME.github.io` (replace `USERNAME` with your GitHub account name). If you prefer a project repository, the URL will be `https://USERNAME.github.io/REPOSITORY/`.
3. Unzip this project on your computer. Upload **the contents** of the unzipped directory into the repository root (`index.html`, `admin.html`, `assets/`, `data/`, `.nojekyll`, and `README.md`). Do not upload the top-level folder alone.
4. Commit the files to the `main` branch.
5. In **Settings → Pages → Build and deployment**, choose **Deploy from a branch**, select **main** and **/(root)**, then **Save**.
6. Your website will be at `https://USERNAME.github.io/`. GitHub Pages may take a few minutes to publish. Check **Actions** or **Settings → Pages** for deployment status.
7. Visit `https://USERNAME.github.io/admin.html` to edit content.

## How to update without programming

1. Open `admin.html` on the **published site** (not as a local file).
2. Select the section in the left navigation. Add, reorder and modify entries.
3. Select **Export backup** to save a local copy of your content before making major changes.
4. For direct publishing, create a **fine-grained GitHub personal access token** at GitHub **Settings → Developer settings → Personal access tokens → Fine-grained tokens**.
5. Restrict the token to **only your website repository** and grant **Contents: Read and write**. Set an expiration date. Do not grant extra repository permissions.
6. Click **Publish to GitHub**. Enter username, repository name, branch (`main`) and token. The editor fetches the current file SHA and commits an updated `data/content.json` through GitHub's official API.
7. Wait for GitHub Pages deployment, then refresh the public website. You can edit manually in GitHub by opening `data/content.json` and clicking the pencil icon too.

**Security:** GitHub Pages is static hosting, so `/admin.html` is publicly accessible. That is not a security boundary. The editor requires your token to perform writes, and the token is held in the current browser tab's memory, not placed in source files, cookies or localStorage. Use the editor only on a trusted device, avoid browser extensions you do not trust, and revoke any token you suspect is compromised. Publishing writes public information to a public repository. GitHub is the source of truth; your local changes do not survive a browser reload unless exported or published.

## Editing locally

Python 3 is sufficient:

```bash
cd research-portfolio
python3 -m http.server 8000
```

Open `http://localhost:8000/` (website) or `http://localhost:8000/admin.html` (editor). Do not open `index.html` directly with `file://`, as fetch may be blocked.

## Content format

Edit `data/content.json` to control everything. Use empty arrays for unfinished sections. Put the actual, verified records in certifications, patents and copyrights before publicly presenting them. Replace any generic career placeholder with confirmed dates and employer names. Add complete publication citations and DOI links once confirmed. Include URLs including `https://`.

For the header and contact buttons: `site.email`, `site.github`, `site.linkedin`, `site.scholar`, `site.orcid`, `site.resume`. CV can be uploaded to `assets/cv.pdf` and referenced as a same-site relative URL such as `assets/cv.pdf`.

### Photos and PDFs

Add your headshot as `assets/profile.jpg` and your CV as `assets/cv.pdf`. The current abstract hero intentionally does not require a profile photo. To add a portrait to the homepage, edit `index.html` and `assets/style.css`, or request a photo variant. Do **not** upload non-public credentials, private contact info, or identity documents to your public repository.

## Optional upgrades

Custom domain and HTTPS through GitHub Pages settings; ORCID/Crossref publication sync via a later GitHub Action; privacy-friendly analytics; contact form via third-party service; multilingual content; searchable paper database. These are not included in the current zero-backend edition.

## Validation checklist

- [ ] Replace generic work experience entries with exact verified information
- [ ] Add your public contact links
- [ ] Check titles, coauthors, DOI links and publication status
- [ ] Add verified certification, patent and copyright information
- [ ] Use your own repository name under Pages settings
- [ ] Test on desktop and mobile after publishing
- [ ] Keep all credentials and GitHub tokens out of public files

## Stack

Vanilla HTML + CSS + JavaScript, GitHub Pages and GitHub REST Contents API. No dependencies or build steps.
