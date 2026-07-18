# The Glass & Crystal Museum — Project Brief (for continuing in a new chat)

Paste this whole document at the start of a new conversation with Claude to continue work on this site with full context.

## What this is
A GitHub Pages digital museum site presenting Nona Dronova's private collection of author's glass and crystal from the Museum of the Pervomaysky Glass Factory.
Repo: `github.com/Nona1960/Private-Museum-of-Glass-Crystal` → deployed at `nona1960.github.io/Private-Museum-of-Glass-Crystal/`
Deployed manually via drag-and-drop upload on GitHub — no build tools, no frameworks.

## Non-negotiable workflow rules (same as Nona's other sites)
1. **Every page is ONE self-contained .html file.** CSS inline in `<style>` in `<head>`, JS inline in `<script>` before `</body>`. No external `style.css`/`script.js`, no `images/` folder.
2. **Images are base64-embedded directly** (`<img src="data:image/jpeg;base64,...">`). Always verify decoded bytes start with JPEG signature `FF D8 FF` before shipping.
3. **Photo processing before embedding:** resize to ~700–780px wide, JPEG quality ~65, then base64-encode.
4. **Dedup check** every new photo batch by md5 against images already used elsewhere on this site (and flag to her if it's a genuine duplicate rather than silently dropping/reusing — she decides). Note: this site legitimately reuses some photos already used on the "Collector's City Apartment" site (different repo) — that's fine, not a same-site duplicate.
5. **No cropping.** Photos are centered using flexbox inside `.photo-row`, never `margin:0 auto` on the image itself.
6. **English only** in all visible site text.
7. **No `href="#"` ever.**
8. **Validation checklist before delivering any page:** tag balance (div/section/header/footer/nav/h1/p/a all open=close, including `</head>`!), zero `href="#"`, zero Cyrillic outside base64 blocks, all embedded images decode to valid JPEG signature, all internal links resolve to files in the delivered set.
9. **Delivery workflow:** do NOT bundle into a zip while reviewing — send each finished/updated page as a standalone file. Full set together only at final GitHub-upload stage.
10. **Attribution rule:** only caption a piece as being by a named artist (e.g. Vladimir Berdnikov) when she has explicitly said so for that specific piece/series. Otherwise use neutral descriptive captions plus "— Pervomaysky Glass Factory" / "...museum collection" without inventing specifics.

## Design system
```
--bg:      #E4EEFA   (background, pale but bright cobalt blue)
--bg2:     #D6E6F7   (secondary background, footer)
--text:    #202B36
--line:    #C9DCEE
--accent:  #C0332C   (coral-red, sampled from a reference photo — used for ALL active/hover buttons)
--hover:   #9C2A22
```
Fonts: Cormorant Garamond (headings/captions, serif, italic for eyebrows/captions) + Inter (body/UI, light weight). Loaded via Google Fonts `@import` in the inline stylesheet.

Layout: max content width 1400px, thin hairline dividers, generous white space.

**Mobile requirement — important, explicitly requested:** compact/tight for mobile app use. Photos are ALWAYS displayed in a single vertical column (one `.photo-row` per image, stacked) — never a grid or masonry layout on this site, at any breakpoint. Burger menu replaces the desktop nav below 1000px. At 640px: smaller headings, tighter padding (20px), footer switches to column layout.

## Site chrome (use on every page)
**Header:** square sun-logo (same logo image reused from Nona's other project sites — "Art of Jewellery" / "Collector's City Apartment" — no border-radius, always square) on the left, stacked with brand name "The Glass & Crystal Museum" (italic serif) + sub-caption "Private Collection of Author's Glass" underneath. To the right, nav pills:
Studio Glass · Crystal Vases · Crystal Goblets · Crystal Tableware
(No explicit "Home" button in desktop nav — clicking the logo goes home. Mobile dropdown nav DOES include "Home" explicitly.)
Active/current page gets the pill filled solid in `--accent` color.

**Footer:** same square sun logo + static (non-link, non-active) caption "Private Museum of Author's Glass & Crystal" on the left. On the right, ONE active link, always highlighted/filled like an active button on every single page (this is intentional — it's the site's single standing footer CTA):
History of the Factory & Collection → `factory-history.html`

Reusable CSS classes already defined and battle-tested: `.photo-row` (centered image, single column, no frame — `.photo-row.wide` for hero images capped at 640px), `.photo-caption` (small italic accent-colored caption under a photo), `.homepage-buttons` (centered button row), `.intro-block` (centered title/eyebrow block), `.bio-block` (left-aligned body text, max-width 760px).

## Page-by-page status

| Page | File | Status |
|---|---|---|
| Home | `index.html` | **Done.** Hero photo (red/amber glass vases shelf) + second photo of the "Blue Birds" Berdnikov set, her intro text about the collection, 4 nav buttons down to the sub-pages. |
| Studio Glass | `studio-glass.html` | **Done.** Her full text on 1970s–80s studio glass artists, then 16 individual photos (one column), each captioned descriptively + "— Pervomaysky Glass Factory, museum collection". |
| Crystal Vases | `crystal-vases.html` | **In progress, she said she'll keep adding more.** Her full "Collection of Soviet Crystal" text, then currently **13 vases / 26 photos** — each vase gets TWO photos stacked vertically (main view, then a detail/close-up of the cutting), captioned with suffix "— Pervomaysky Glass Factory, 1970s–1980s" on the main shot. Some early pairs in the sequence don't have a clean "main vs. detail" distinction (both shots are close-ups) — captioned honestly/descriptively rather than guessing which is which. |
| Crystal Goblets | `crystal-goblets.html` | **Not started.** |
| Crystal Tableware | `crystal-tableware.html` | **Not started.** |
| History of the Factory & Collection | `factory-history.html` | **Not started** (footer link target). |

## Open items for next chat
- Continue adding vases to Crystal Vases as she sends more photos (same main+detail pairing pattern).
- Build Crystal Goblets, Crystal Tableware, and History of the Factory & Collection pages once she has text/photos ready.
- Confirm repo name/description are already set (yes — repo exists and README already created by her on GitHub).
- Once all pages are approved, do a full cross-page validation pass (tag balance, links, dedup) before final delivery of the complete file set for GitHub upload — she uploads by drag-and-drop directly, files should be named exactly: `index.html`, `studio-glass.html`, `crystal-vases.html`, `crystal-goblets.html`, `crystal-tableware.html`, `factory-history.html`.
- Note: when delivering `index.html` for download, name the file something else (e.g. `index-glass-museum.html`) to avoid overwriting other projects' `index.html` files in the output directory — she renames it to `index.html` herself right before uploading to GitHub.
