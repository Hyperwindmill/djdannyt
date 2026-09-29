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

## Philosophy (inherited, not negotiable)

- **AI transparency is the strategy.** The AI-made releases are declared as such, the
  hand-made ones say "hand-made". The site says it plainly; never soften it.
- **Photos are real photos.** No AI-generated portraits, ever. Until a real console photo
  exists the page shows a placeholder, not a substitute. (The graffiti banner is brand
  artwork, not a portrait — it is fine.)
- **No audio masters and no rendered video in git.** Music is heard through store embeds
  and links; media stays in `../music-production`. Small web-sized images only.
- **Lazy-correct.** One `index.html`, inline CSS/JS, no build step, no framework, no
  analytics. Add a tool the second time it is needed, not the first.
- **Verify, don't recall.** Store links and titles come from the sister repo's canonical
  IDs or the store APIs (`api.deezer.com`, `itunes.apple.com/lookup?upc=`), never from
  memory.
- **English on the page** (the tracks are English, the audience is global); Italian with
  Daniele in chat.

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
- Instagram and YouTube channel URLs are not recorded in the sister repo yet: add them
  to the links row once Daniele gives them (TikTok is `@djdannyt88`).
- A Blender-rendered visual from `../music-videos` could replace the static hero later;
  the old GLSL shader is NOT the way (low quality — Daniele, 2026-09-29).
- **Pressure Zone cover links to its HyperFollow (pre-save) until release day 2026-10-02**:
  then swap it to the Spotify album URL (find the ID on the public artist page:
  `curl -s -A Mozilla/5.0 https://open.spotify.com/artist/210zlGpeVnSE9ojHMKoVNb | grep -oE '/album/[A-Za-z0-9]{22}'`,
  confirm the title with `https://open.spotify.com/oembed?url=…`). song.link's public API is dead (401).
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

GitHub Pages serves `main` at https://hyperwindmill.github.io/djdannyt/ — a push is a
deploy. Check locally first: `python3 -m http.server 8080` in this folder.
Commit with the repo-local identity (GitHub noreply, already configured).
