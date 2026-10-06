# finnlimjc.github.io

Personal website of Finn Lim, built with Jekyll and the [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) theme and served at https://finnlimjc.github.io.

## Structure

| Page | Source | Content |
| --- | --- | --- |
| Profile (`/`) | `index.html` | Skills, education, personal projects |
| School Projects | `school-projects.html` | Academic projects |
| Academic Experience | `academic-experience.html` | Research and teaching assistant roles |

Content lives in `_data/` (`education.yml`, `projects.yml`, `experience.yml`); every entry is rendered by `_includes/entry.html`. Skills are listed in `_config.yml`. Styling overrides are in `assets/css/main.scss`.
