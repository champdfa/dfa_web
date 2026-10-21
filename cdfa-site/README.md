# Champlain College Digital Forensics Association website

A Jekyll site built for GitHub Pages. It has three main parts:

- **Home** (`index.html`): a hero section, the next few upcoming events, latest news and recent presentations.
- **News & Events** (`_posts/`): announcements and event posts. Anything with an `event_date` shows up under "Upcoming" until that date passes.
- **Presentations** (`_presentations/`): one page per meeting night with the slides embedded, plus notes, links and lab files.

## Setting it up on GitHub

1. Create a repo and push these files to it.
   - If the repo is named `<org-or-user>.github.io`, the site lives at the root and you can leave `baseurl` empty.
   - Otherwise (e.g. `cdfa/website`), open `_config.yml` and set `baseurl: "/website"`.
2. In the repo, go to **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
3. Edit `_config.yml`: meeting day, time, room, club email and social links. Leave a link as `""` to hide it.
4. Edit `about.md` with your officers and anything else you want on the About page.

The site will be live at the URL shown on the Pages settings screen within a minute or two of each push.

## Adding an event or news post

Create a file in `_posts/` named `YYYY-MM-DD-short-title.md`, using **today's date** (the date you're posting it), not the event date. Files dated in the future are hidden until that day.

```markdown
---
title: "Workshop: Windows Artifacts"
event_date: 2026-10-28 19:00:00 -04:00   # leave this out for a plain news post
location: Room 123
presenter: Jane Doe
rsvp: https://forms.gle/...            # optional
summary: One or two sentences shown on the cards.
---

The full announcement goes here, in Markdown.
```

Use `-04:00` for dates between mid-March and early November (EDT) and `-05:00` for the rest of the year (EST).

## Adding a presentation

1. Put the slides in `assets/slides/` (PDF works best), e.g. `assets/slides/2026-10-28-windows-artifacts.pdf`.
2. Create `_presentations/2026-10-28-windows-artifacts.md`:

```markdown
---
title: "Windows Artifacts: Prefetch, Shellbags & LNK Files"
date: 2026-10-28
semester: Fall 2026                     # groups talks on the Presentations page
presenter: Jane Doe
tags: [windows, artifacts]
slides: /assets/slides/2026-10-28-windows-artifacts.pdf
recording: https://youtube.com/...      # optional
materials: /assets/labs/windows-lab.zip # optional
summary: One or two sentences shown on the list page.
---

Notes, commands, and links from the night.
```

**Google Slides instead of a PDF:** in Google Slides choose *File → Share → Publish to web → Embed*, copy the link out of the `src="..."` part, and paste it as `slides:`. The page embeds it automatically.

Keep PDFs under about 50 MB; GitHub rejects files over 100 MB.

## Keeping "Upcoming" accurate

GitHub Pages only rebuilds when someone pushes, and the upcoming list is worked out at build time. The workflow in `.github/workflows/daily-rebuild.yml` asks Pages to rebuild every morning so past events drop off on their own. If it ever fails, go to **Settings → Actions → General → Workflow permissions** and make sure Actions are allowed. You can also run it by hand from the **Actions** tab.

## Previewing locally (optional)

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

## Changing the look

All styling is in `assets/css/main.scss`. The colors are variables at the top, so changing `--accent` and `--hero-accent` re-colors the whole site. Navigation links live in `_data/navigation.yml`.
