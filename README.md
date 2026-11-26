# kaitaolai.github.io

Academic website of Kaitao Lai, built with the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme (v1.2, MIT licence).

Content:

- `_pages/about.md`: home page text; `assets/img/prof_pic.jpg`: photo (EXIF removed)
- `_bibliography/papers.bib`: publications, BibTeX from the DOIs; `selected = {true}` puts a paper on the home page
- `_projects/`: one page per project
- `_data/cv.yml`: CV page (from the master CV, without contact details)
- `_data/socials.yml`: profile links (no email or phone, by choice)

Build and preview locally with Docker:

```bash
docker run --rm -v "$PWD":/srv/jekyll -w /srv/jekyll -e JEKYLL_ENV=production amirpourmand/al-folio:latest bundle exec jekyll build
cd _site && python3 -m http.server 4000      # http://localhost:4000
```

On GitHub, `.github/workflows/deploy.yml` builds the site on each push to `main`; GitHub Pages serves it at https://kaitaolai.github.io.
