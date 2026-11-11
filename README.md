# Academic site

A Jekyll site. GitHub Pages builds it automatically when you push, so there is nothing to install or run.

## What to edit

| To change | Edit this file |
|---|---|
| Add or update a paper, move it from working paper to published | `_data/papers.yml` |
| Add a job or TA role | `_data/experience.yml` |
| Add a degree | `_data/education.yml` |
| Skills list | `_data/skills.yml` |
| About text and the facts table | `_data/about.yml` |
| Email, LinkedIn, location, CV link, Scholar/SSRN/ORCID/GitHub links, research interests | `_config.yml` |
| Add a page to the nav bar | `_data/navigation.yml` (plus a new `.html` file) |
| Colors, fonts, spacing | `assets/css/style.css` |

Everything else (nav bar, footer, page layout) is shared and rarely needs touching. The footer shows your contact details on every page, from `_includes/footer.html`.

## Adding a paper

Open `_data/papers.yml`, delete the `[]` line, and add:

```yaml
- title: Short Paper Title
  status: working_paper      # working_paper | work_in_progress | published
  year: 2026
  coauthors: Coauthor One    # optional
  abstract: Two or three sentences.   # optional
  pdf: /papers/short-paper-title.pdf  # optional; file goes in the papers/ folder
  ssrn: https://papers.ssrn.com/...   # optional
```

Newest first within each status. When the paper is accepted, change `status` to `published` and add `venue: Journal Name`. It moves to the Publications section on its own.

## Adding a CV

Put `cv.pdf` in the repo root and set `cv_file: /cv.pdf` in `_config.yml`. A CV link then appears on the home page and in the footer.

## Splitting Teaching into its own page later

1. Create `teaching.html` with this front matter, and list your courses with a loop like the one in `experience.html`:
   ```
   ---
   layout: page
   title: Teaching
   ---
   ```
2. Add `- title: Teaching` / `url: /teaching.html` to `_data/navigation.yml`.
3. In `_data/experience.yml`, move the teaching entries to a new `_data/teaching.yml`, or keep the `category: teaching` tag and filter on it in the new page.

## Hosting

1. Create a repo named `<your-username>.github.io` and upload the contents of this folder to its root (keep the folder names that start with an underscore).
2. Settings → Pages → Source: `main` branch, root folder.
3. After about a minute the site is live at `https://<your-username>.github.io`. After every later edit, wait that minute and refresh.

If the site is at `<username>.github.io/<repo>` instead, set `baseurl: "/<repo>"` in `_config.yml`.

Do not add a file named `.nojekyll`. It turns the build off.

If a page looks broken after an edit, the repo's Actions tab shows the build error, which usually points at a spacing mistake in one of the `.yml` files (YAML needs consistent indentation).

## Previewing on your own computer (optional)

Install Ruby, run `bundle install` once, then `bundle exec jekyll serve` and open http://localhost:4000.
