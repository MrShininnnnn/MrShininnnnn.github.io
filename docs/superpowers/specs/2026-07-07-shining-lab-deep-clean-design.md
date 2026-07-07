# Shining Lab Site Deep Clean — Design

## Context

This repo (`mrshininnnnn.github.io`) is an al-folio Jekyll site that has never been fully customized past initial setup — it still carries theme demo content (placeholder project/post, Albert Einstein CV data), a dead redirect to the author's separate personal Google Sites homepage, and a stale third-party script dependency (`polyfill.io`, already fixed in a prior session after it was found serving a credential-phishing prompt).

The site's role has been clarified: this is the home of **Shining Lab**, distinct from the author's personal academic page (which lives on Google Sites and may be shut down after graduation). This site should stand on its own as the lab's durable, canonical home — not a mirror of the personal site.

## Goals

1. Remove remaining security/staleness risk from third-party script dependencies.
2. Strip unedited al-folio theme demo content.
3. Populate real lab content (news, projects, about) sourced from the author's Google Sites page, reframed around the lab rather than personal biography.
4. Clean up dead config (Disqus, personal-only social accounts).

## Non-goals

- No CV page (explicitly declined — this is a lab site, not a personal CV).
- No full personal timeline import — only research/lab milestones, not personal life events (graduations, job changes, family).
- No new "current members" roster beyond the PI — lab has one member (Ning Shi) plus past collaborators, not current lab members.

## Design

### 1. Security fixes

**Vendor `bootstrap-toc` locally.** It's currently loaded from `cdn.rawgit.com`, a CDN that shut down in 2019 — an abandoned/hijackable domain, the same risk class as the `polyfill.io` incident. Rather than swap to another CDN, vendor the two minified files (v1.0.1) into `assets/vendor/bootstrap-toc/bootstrap-toc.min.css` and `.min.js`, and point [_includes/head.html](_includes/head.html) and [_includes/scripts/misc.html](_includes/scripts/misc.html) at the local paths. This removes the third-party dependency for this small, unmaintained library entirely.

**Add missing SRI integrity hashes** to script/link tags currently missing them:
- `bootstrap-table` CSS link (in `_includes/head.html` or wherever it's declared)
- `imagesloaded` script (masonry companion, in the scripts includes)
- MathJax script tag ([_includes/scripts/mathjax.html](_includes/scripts/mathjax.html))

**Fully purge Disqus** (deprecated, superseded by the already-active Giscus integration):
- Delete `_includes/disqus.html`
- Remove its include calls from `_layouts/post.html` and `_layouts/distill.html`
- Remove `disqus_shortname: shininglab` from `_config.yml`

### 2. Strip al-folio boilerplate

Delete unedited theme demo content, confirmed unreferenced elsewhere in the site (no `_pages/cv.md` exists, so the CV layout/data/includes are fully dangling):
- `_projects/0.md` (generic "project 1" demo page)
- `_posts/0.md` (lorem-ipsum-style "hipster" demo post)
- `_data/cv.yml` (unedited Albert Einstein demo data)
- `_layouts/cv.html`
- `_includes/cv/` (list.html, map.html, nested_list.html, time_table.html)

### 3. News content

Replace `_news/0.md` (a stub that just redirects visitors to the Google Sites personal page) with individual news entries for **research/lab milestones only**, sourced from the Google Site's news feed. Personal life events (graduations, job changes, family) are excluded — this is the lab's public record, not a personal diary.

Each entry becomes its own file at `_news/YYYY-MM-DD-slug.md` following al-folio convention (`layout: post`, `inline: true`, `related_posts: false`), one line of content each. Full list to import (title/date, condensed to a single descriptive line per entry):

- 2019-09-01 — Launched Shining Lab
- 2021-06-02 — Paper accepted to Interspeech 2021
- 2021-08-26 — Paper accepted to Findings of EMNLP 2021
- 2022-10-06 — Two papers accepted to Findings of EMNLP 2022
- 2022-10-11 — Paper accepted to Fifth BlackboxNLP Workshop, EMNLP 2022
- 2022-12-23 — Shared findings at Amii AI Seminar
- 2023-01-21 — Paper accepted to EACL 2023
- 2023-05-01 — Paper accepted to Findings of ACL 2023
- 2023-05-22 — Survey paper published
- 2023-10-07 — Paper accepted to EMNLP 2023
- 2023-11-29 — Received Alberta Graduate Excellence Scholarship
- 2024-02-29 — Received 2024 Upper Bound Talent Bursary
- 2024-03-19 — Team placed top-3 in 16 language/track settings at SemEval 2024
- 2024-04-22 — Three papers accepted to *SEM 2024
- 2024-05-15 — Paper accepted to ACL 2024
- 2024-09-06 — Best Poster Award at Reverse EXPO
- 2024-09-20 — Shared findings at Amii AI Seminar
- 2024-11-29 — Paper accepted to COLING 2025
- 2024-12-06 — Received Alberta Graduate Excellence Scholarship (second time)
- 2025-02-16 — Team achieved top rankings in the COMET track, SemEval 2025 Task 2
- 2025-02-29 — Received 2025 Upper Bound Talent Bursary
- 2025-04-24 — Received 2025 Graduate Student Teaching Award
- 2025-06-17 — Presented research at Tea Time Talk (RLAI)
- 2025-07-10 — Shared research at Undergraduate CS Research Seminar
- 2025-07-25 — Passed Ph.D. candidacy examination
- 2025-08-20 — Paper accepted to EMNLP 2025
- 2026-01-04 — Paper accepted to EACL 2026
- 2026-03-03 — Team placed 2nd overall at SemEval-2026 Task 5
- 2026-04-01 — Book published by Springer
- 2026-04-08 — Paper accepted to Canadian AI 2026
- 2026-07-04 — SemEval-2026 paper received Best Paper Award

No config changes needed for display — `announcements.limit: 5` already keeps the homepage to the 5 most recent; the full set lives in `/news/`.

### 4. Projects content

Replace the placeholder with 2–4 real entries reflecting Shining Lab's actual research focus (computational linguistics, NLP, reinforcement learning, multilingual systems, LLM analysis/evaluation), drawn from the author's stated research interests and recent publication themes (SemEval multilingual tasks, LLM evaluation). Descriptions will be short and directionally accurate; the author can refine specifics/links afterward.

### 5. About page

Reframe [_pages/about.md](_pages/about.md) to lead with Shining Lab's identity and mission first, with the PI's bio presented under a members framing (rather than the current personal-bio-first structure). Add a **Collaborators** section listing Jie Fu (IQuest Research, ex-Mila) and Zhouhan Lin (SJTU/Mila) as past/external collaborators — clearly distinguished from lab membership.

### 6. Config cleanup

Remove from `_config.yml`:
- `twitter_username: MrShininnnnn` (personal account)
- `medium_username: mrshininnnnn` (personal account)
- `disqus_shortname: shininglab` (dead, superseded by giscus)

## Testing / Verification

- `bundle exec jekyll build` (or `docker-compose up`) completes without errors after each content/config change.
- Visual check in local dev server: homepage news list renders, `/news/` archive shows full list, `/projects/` shows new entries, About page renders correctly, no console errors for missing local vendor assets.
- Verify no remaining references to `polyfill.io`, `rawgit.com`, or `disqus` (config/includes/layouts) via grep.
- No git push — local verification only; the user pushes/deploys themselves.
