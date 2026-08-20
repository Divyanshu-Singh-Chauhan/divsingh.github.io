# divsingh.github.io

Personal portfolio for Divyanshu Singh Chauhan — robotics and autonomy engineering.
Built with [Jekyll](https://jekyllrb.com/) and the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) remote theme, hosted on GitHub Pages.

Live: <https://divyanshu-singh-chauhan.github.io/divsingh.github.io/>

## Layout

```
_config.yml              site config, author profile, SEO
_data/navigation.yml     top nav
index.md                 homepage (splash layout)
_pages/
  projects.md            all project write-ups (anchors linked from the homepage)
  publications.md
  resume.md              both résumé PDFs
  contacts.md
  404.md
assets/
  css/main.scss          custom styles layered over Minimal Mistakes
  images/                hero banner, social card, photos, figures
  docs/                  résumé PDFs, project reports, figures
```

## Running locally

```bash
bundle install
bundle exec jekyll serve
# http://localhost:4000/divsingh.github.io/
```

## Notes

- The site is published as a **project page**, so `baseurl` is `/divsingh.github.io`.
  Renaming the repo to `divyanshu-singh-chauhan.github.io` gives a clean root URL —
  if you do that, set `baseurl: ""` in `_config.yml`.
- Internal links use `{{ "/path/" | relative_url }}` so they keep working under the baseurl.
- Project anchors on `/projects/` are set explicitly (`{: #botlab-slam}`); the homepage
  links to those anchors, so don't rename them without updating `index.md`.
