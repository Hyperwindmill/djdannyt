# djdannyt — DJ Danny-T public site (EPK)

The public face of **DJ Danny-T** (Daniele's DJ/producer identity): a one-page electronic
press kit for promoters, jam organizers, local press and other DJs who ask "mandami
qualcosa". Hosted on GitHub Pages from this repo (public by nature — nothing private
lands here).

This repo has a sister: **`../music-production`** holds the music, the release state, the
artist doctrine and the way of working with Daniele. **Read there before touching this
site** — this repo lays out, it never invents:
- `CLAUDE.md` — the voice (Italian with him, 1-3 short paragraphs, one recommendation,
  commit and push without asking, never amend/rebase/reset), the canonical facts (artist
  name `DJ Danny-T` with the hyphen, store IDs, links) and the hard rules.
- `docs/artist-profile.md` — who he is, the bio material, the AI-transparency doctrine.
- `docs/release-status.md` — what is live and what is in flight: the releases section of
  the page mirrors it, never the other way round.

## Public repo: nothing unapproved leaves this machine

This repo is PUBLIC, so every pushed branch is public too, not just `main`. Material that is
not approved yet (a photo someone must OK, a draft text) stays on a LOCAL branch and is never
pushed until Daniele confirms. (2026-09-29: the press-photo branch was pushed by mistake and
removed from GitHub.)

## Philosophy (inherited, not negotiable)

- **AI transparency is the strategy.** The AI-made releases are declared as such, the
  hand-made ones say "hand-made". The site says it plainly; never soften it.
- **Photos are real photos.** No AI-generated portraits, ever. Until a real console photo
  exists the page shows a placeholder, not a substitute. (The graffiti banner is brand
  artwork, not a portrait — it is fine.)
- **No audio masters and no rendered video in git.** Music is heard through store embeds
  and links; media stays in `../music-production`. Small web-sized images only.
- **Lazy-correct.** One bilingual source, inline CSS, no JS, no framework, no analytics; the
  only tooling is `build.py` (Python stdlib). Add a tool the second time it is needed, not the first.
- **Verify, don't recall.** Store links and titles come from the sister repo's canonical
  IDs or the store APIs (`api.deezer.com`, `itunes.apple.com/lookup?upc=`), never from
  memory.
- **Two languages, one source** (decided 2026-09-29): English at `/`, Italian at `/it/`.
  Promoters and press who book him are Italian; pool DJs and store listeners are not. The
  Italian is rewritten in his register, never translated word for word ("Mistakes included." →
  "Errori inclusi.", "Then I got back to work." → "Poi mi sono rimesso al lavoro."). Italian
  with Daniele in chat.

## How to edit (read before touching any page)

- **Edit `src/index.html` only.** `index.html` and `it/index.html` are GENERATED and say so in
  their first lines.
- Every piece of text that differs by language is written `[[english||italiano]]`, side by side,
  so changing one reminds you of the other. `@/` is the path to the site root (assets, language
  links). Text that is the same in both languages (names, venues, genres) is written once.
- `python3 build.py` writes both pages; it fails on an unbalanced marker. The pre-commit hook in
  `.githooks/` runs it and stages the output, so a commit can never ship a stale page. **On a
  new clone, enable it once:** `git config core.hooksPath .githooks`.
- Why not Pug or another template engine: npm and a template language for one page. Why not a
  JS language toggle: link previews (WhatsApp, Facebook) read the meta tags without running JS,
  so the Italian link would preview in English.

## Layout of the page (index.html)

**Essential by design** (Daniele, 2026-09-29: "le cose in dubbio, via; informazioni utili,
overview"): hero (graffiti banner + one-line timeline) → who (two short paragraphs + facts card
with the copy-paste bio) → music (Spotify embed, store chips, three release cards) → live (a
dated list, newest first — the 2013–2025 gap shows by itself) → tech rider (three short lists)
→ booking (mail + chips). Plain headings; the only wordplay kept is his own "Open format,
strong roots." Before adding anything, ask: is it verified, and does a promoter need it? If
either answer is no, it stays out. Style lives in the graphics, not in the sentences.

## Open items

- Real console photo (from Kamo's night, background removal to evaluate): the "Press photos"
  section was removed with the placeholders; bring it back only with real files.
- Instagram URL not recorded yet (YouTube is `@djdannytGE`, TikTok is `@djdannyt88`).
- A Blender-rendered visual from `../music-videos` could replace the static hero later;
  the old GLSL shader is NOT the way (low quality — Daniele, 2026-09-29).
- **Pressure Zone cover links to its HyperFollow (pre-save) until release day 2026-10-02**:
  then swap it to the Spotify album URL (find the ID on the public artist page:
  `curl -s -A Mozilla/5.0 https://open.spotify.com/artist/210zlGpeVnSE9ojHMKoVNb | grep -oE '/album/[A-Za-z0-9]{22}'`,
  confirm the title with `https://open.spotify.com/oembed?url=…`). song.link's public API is dead (401).
- **Logo rule (2026-09-29)**: the DT monogram is drawn black-on-light (its thin inline is a gap, not
  a stroke). NEVER invert it to white: on dark it becomes white-black-white and reads as two
  shapes. On dark backgrounds use `assets/badge.svg` (black monogram on an off-white disc, like a
  record label). Source files: `../music-production/artwork/dannyt-logo.svg` (use) and
  `dannyt-logo-inkscape.svg` (edit).
- **PINNED — small-size logo (Daniele, 2026-09-29)**: below a certain size the monogram's thin
  inline gap turns into noise, on the badge too; only large it reads well. Needs a small variant
  (silhouette without the inline gap, drawn in `dannyt-logo-inkscape.svg`) for favicon, avatars,
  footer. Not started.
- Custom domain: optional, `CNAME` file when he buys one.
- **Voice rule (Daniele, 2026-09-29)**: the page speaks in FIRST person, deadpan, his register
  ("Mistakes included."). Third person only inside the labelled "Short bio — copy and paste
  it" block, made of verifiable facts, no adjectives. Never write self-praise disguised as
  editorial ("he may be the only DJ in the room…" was cut for exactly that). Never say anything
  at another DJ's expense, not even implicitly ("the billed DJs did not show" was cut: the
  scene is small and reads this page).
- **The 2013–2025 break is stated, never hidden** (Daniele, 2026-09-29: "onesti e trasparenti,
  non siamo venditori"). The live history is 2009–2013; the page says so, names the long break
  (day job, marriage, a family) and presents 2026 as the comeback. No continuous-career phrasing
  ("twenty years…"), no disclaimer about the tone: the honesty does that job.
- Past gigs to cite (dates to be found by Daniele, never guessed): the breaking contest he
  played in Varazze (DONE, on the page: OBC – Okult Breaking Contest, 19 May 2012, Molo del Surf, credited "DJ: Danny-T"); opening for DJ Double S at the Ghost; resident at AQA (Friday opener,
  full Saturday night) — which years. Add to "Live" only with the dates.

## Publishing

GitHub Pages serves `main` at https://hyperwindmill.github.io/djdannyt/ (Italian:
`/djdannyt/it/`) — a push is a deploy. Check locally first: `python3 -m http.server 8080` in
this folder. Stop the server by port (`fuser -k 8080/tcp`), never with `pkill -f` on a pattern
that also matches the calling shell.
Commit with the repo-local identity (GitHub noreply, already configured).
