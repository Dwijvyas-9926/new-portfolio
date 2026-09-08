# Dwij Vyas — Portfolio

Three pages, one content file, no build step.

| File | What it is |
| --- | --- |
| `index.html` | The portfolio — the 3D temple world, five chapters |
| `recruiter.html` | Recruiter mode — the whole record on one printable page |
| `admin.html` | The editor — sign in, change content, publish |
| `content.json` | **All content lives here.** Both pages read it at load |

Everything else is assets: `secret-pathways-assets/` (the world),
`inner-green-assets/` (fonts), the résumé PDF, project images.

---

## Deploying to Vercel

**1 · Put these files in a GitHub repository.**
Drop the whole folder in at the repo root. Nothing needs compiling.

**2 · Import the repo at [vercel.com/new](https://vercel.com/new).**
Framework preset: **Other**. Leave build command and output directory empty —
this is static HTML, so there is nothing to build. Deploy.

**3 · Point your domain at it** (optional) under Settings → Domains.

That is the whole deployment. Every push to `main` redeploys automatically.

---

## Making live changes

Open `/admin.html` on the deployed site and sign in.

Edits save to your browser immediately, so you can preview them against the
real portfolio before anyone else sees them. **Publish** is what makes them
live: it writes `content.json` back to GitHub, GitHub tells Vercel, and Vercel
redeploys. The change is public in about a minute.

### One-time setup for Publish

Publish needs permission to write to your repository.

1. GitHub → Settings → Developer settings → **Fine-grained personal access
   tokens** → Generate new token.
2. Repository access: **Only select repositories** → pick this repo.
3. Permissions → Repository permissions → **Contents: Read and write**.
   That is the only permission needed.
4. Copy the token — GitHub shows it once.
5. In the admin, open the **Publish** panel and fill in:
   - Repository — `your-username/your-repo`
   - Branch — `main`
   - File path in repo — `content.json` (adjust if it sits in a subfolder)
   - Personal access token — paste it

The token is stored in your browser only. It is never committed, and it is not
in any of these files. If you clear your browser data you will re-enter it.

### If you would rather not use a token

The admin's **Export** button downloads `content.json`. Commit that file to
the repo yourself and Vercel redeploys the same way. Slower, but nothing to
store.

---

## Notes

- **Images** are resized to 1280px and embedded in `content.json` on upload.
  The first image on a project is its display image on the work index; use
  **Make display** on any other image to promote it.
- **The résumé** is a real file, not content — replace
  `dwij-vyas-resume.pdf` in the repo to update it.
- **`content.json` is the single source of truth.** Both the portfolio and
  recruiter mode read it, so a change appears in both.
