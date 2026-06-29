# Shih Lab website (static recovery)

A static recovery of the Shih Lab website (`nature.berkeley.edu/shih-lab/`),
rebuilt from the [Wayback Machine](https://web.archive.org/web/20250620043649/https://nature.berkeley.edu/shih-lab/)
snapshot of **20 June 2025** so it can be served from GitHub Pages.

## What's here

Six main pages plus 26 individual lab-member bio pages, kept at directory-style
paths so the links work both at a project subpath
(`user.github.io/shih-lab-site/`) and later at a custom domain:

| Page | Path |
|------|------|
| Home | `index.html` |
| Research | `about/` |
| People | `people/` |
| Publications | `publications/` |
| News | `news/` |
| Join Our Lab | `join-our-lab/` |
| Lab-member bios (×26) | `lab-members/<name>/` |

Theme CSS/JS, fonts, and images live under `wp-content/` and `wp-includes/`,
mirroring the original WordPress layout. All internal links and asset
references are **relative**, so nothing is tied to a specific domain.

### Notes / known limitations

- Tracking/analytics (Jetpack stats, WordPress emoji detection, speculation
  prefetch) were stripped. Google Fonts is still loaded from Google.
- Two homepage slider images (`Ruby_gradient`, `rando_cluster`) were never
  successfully captured by the archive, so those two slides were dropped; the
  slider cycles the remaining intact images.
- Font Awesome webfonts weren't in the archive, so the identical Font Awesome
  4.7.0 files were sourced from cdnjs.
- A few cosmetic/non-rendered assets missing from the archive (lightbox CSS, an
  IE-only shim) fall back to the Wayback Machine and degrade silently.
- Member bio links to outside profiles (LinkedIn, email) and publication DOIs
  remain external, as on the original site.

## Deploying to GitHub Pages

1. Create a repo and push this directory.
2. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*,
   Branch = `main`, folder = `/ (root)`.
3. The site publishes at `https://<user>.github.io/<repo>/`.

### Custom domain (later)

Point a DNS `CNAME` (or apex `A`/`ALIAS`) record at GitHub Pages, then add the
domain under **Settings → Pages → Custom domain**. GitHub will create a `CNAME`
file in the repo. Because all links here are relative, nothing else needs to
change.

The `.nojekyll` file disables Jekyll processing so the `wp-*` directories are
served verbatim.
