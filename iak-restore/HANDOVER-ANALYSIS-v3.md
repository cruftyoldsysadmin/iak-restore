# İstanbul Avrupa Korosu — website recovery and rebuild

**Handover for Ece — prepared 14 September 2026**

Self-contained: assumes no prior knowledge. Detailed enough for Claude to act
on directly.

---

## 1. Situation

Weebly is shutting down in Türkiye. The choir's website,
`www.istanbulavrupakorosu.org`, ran on Weebly since 2013.

| Date | What happens |
|---|---|
| **27 September 2026** | Weebly unpublishes the site |
| **26 December 2026** | Weebly account access ends |

The site is **already down**. The domain still points at Weebly and Weebly
returns a 404 there.

Weebly's data export turned out to be a database dump, not a website backup —
CSV tables only, no pages, no images, no styling. It could not rebuild
anything. Everything below came from two other places: the Internet Archive
(page content) and Weebly's own file servers (media, pulled directly before
the shutdown).

---

## 2. What was recovered

**Media — 593 files, 1.88 GB**, downloaded from Weebly at original quality.
Weebly stored three copies of most files under decorated names; removing
duplicates by content hash took 1,594 files down to 593 distinct ones.

**Pages — 44 pages, 8,907 words**, from the Internet Archive, cross-checked
against Weebly's own page list so structure and SEO fields match the real site.

**877 email addresses** — see section 7, there is a catch.

Where the work is:

| Page | Words | Files used |
|---|---|---|
| Hakkında | 2,370 | 1 |
| Etkinlikler | 780 | 21 |
| Events | 728 | 17 |
| Christmas Carols | 649 | 63 |
| Daphnis et Chloe | 561 | 47 |
| Materyaller | 529 | 50 |

---

## 3. What was lost permanently

**1,666 membership application submissions.**

The export kept the applications' structure — all 29 Turkish questions, and
the fact that 1,401 people answered — but replaced every answer with a
placeholder of its type. Across 15,297 answer rows there are exactly two
distinct values: `@.` where an email was, `weebly/uploads` where an attachment
was.

Checked across six routes: the Weebly dashboard, three internal APIs, the
classic editor endpoints, and the raw export. Not retrievable. Weebly support
has already been asked.

**About 51 images** referenced by old pages no longer exist anywhere — deleted
from Weebly years before the shutdown. Listed in `missing-files.txt`.

---

## 4. Scope of the first build

The member-only section is **not** being rebuilt. Rehearsal audio, scores and
practice files now live in Google Drive, shared with the choir. That decision
removes 11 pages and 1.76 GB from the website entirely.

What is left is small:

| | |
|---|---|
| Core pages to build | **10** |
| Words | 5,170 |
| Images | 76 files, **4.4 MB** |

| # | Page | Words |
|---|---|---:|
| 1 | Ana Sayfa | 44 |
| 2 | Hakkında | 2,370 |
| 3 | Galeri | 10 |
| 4 | Etkinlikler | 780 |
| 5 | Üye Başvuru — *embed the Google Form here* | 57 |
| 6 | İletişim | 15 |
| 7 | Sponsor | 5 |
| 8 | Events *(English)* | 728 |
| 9 | Gallery *(English)* | 10 |
| 10 | Müzik Terimleri *(replaces 17 letter pages)* | 1,151 |

**The application form is a Google Form.** It embeds into whichever page, and
responses land in a Sheet the choir owns. This is deliberate: 1,666 applications
were lost because Weebly held them and stripped them on export. A Google Form
cannot fail that way, and it stays portable if the website moves again. It also
takes "does this builder handle forms well" out of the platform decision.

### Deferred: five repertoire pages

Christmas Carols, Zelenka Bach Byrd, Dvořák, Mahler and Rossini look like
content pages but are really file lists — 61 MIDI files, 20 MP3s, a few PDFs.
Their material is in Drive now. Rebuild them only if you want public pages that
link out to Drive folders.

### The glossary was combined

The old site had 17 per-letter pages (A, B, C … U-V). They are now one
**Müzik Terimleri** page: 141 terms with definitions, 104 without, 245 total.

This fixes a fault that was live on the old site for years. Terms and
definitions sat in two separate side-by-side text blocks, aligned only while
every definition fitted on one line. `Allegro`'s definition wraps, so from there
down every definition displayed against the wrong term — the page showed
`Andante` defined as "sevimli, okşayıcı", which is actually *Amabile*. A single
table cannot drift.

The glossary was also never finished: A–L have definitions, M onward are bare
word lists. The `O` page was six words on an otherwise empty page.

**Needs ten minutes from a musician:** letters **C** and **F** have more terms
than definitions, so the pairing there is positional guesswork. Flagged in the
page file itself.

---

## 5. Hosting alternatives

Checked against each vendor's own documentation. The hard requirements are:
takes 1.88 GB (or ~600 MB after the scope section), accepts unusual file types
(22 `.nwc` scores, 31 `.rar`, 47 `.zip`, 88 `.mid`), allows a 97 MB file,
supports a members-only area, and is editable by a non-technical volunteer.

### 1. Wix — closest to the Weebly experience
Drag-and-drop editor, proper themes, **Turkish interface and Turkish phone
support**. Light 2 GB / Core 50 GB / Business 100 GB, **unlimited bandwidth**
on all. Has both members-only pages and password-protected pages, so
`Üye Girişi` can be rebuilt properly.
**Risk:** their docs will not confirm `.zip`, `.rar`, `.nwc` support. That is
53 files. Test before committing. File Share app caps at 500 MB per file.

### 2. Google Sites + Google Drive — cheapest, best at files, plainest site
Free via Google for Nonprofits, **which is available in Türkiye**. Drive takes
any file type without argument and its sharing permissions give you the
members-only area. Custom domain works.
**Trade-off:** Google's own product page calls Sites *"team and project
websites"*. You cannot control margins, padding or layering; elements are
locked in fixed positions; few themes; forms must come from Google Forms.
It will look plainer than the old site.
**One strong point:** a Google Form drops responses into a Sheet you own. The
membership form *is* a form, and you just lost 1,666 applications because
Weebly held them. That failure cannot repeat.

### 3. WordPress — ruled out by the choir
Technically capable and cheap ($4–25/mo), with the best content API of any
option. **Excluded on maintenance and security grounds**: it needs ongoing
patching and plugin-vulnerability management, and nobody on the committee wants
to be a sysadmin. This is a reasonable call, not a technical limitation.

### 4. Jimdo — simple European builder
Storage scales by plan, up to 500 GB on higher tiers, which is ample.
Positioned at small businesses and non-technical users.
**Unverified:** their help centre blocks automated access, so I could not
confirm which file types the download element accepts, or the members-area
details. Worth a look but check those two points directly.

### 5. Hostinger Website Builder — cheapest paid option
From **$2.99/month** on a 48-month commitment, 300+ templates, drag-and-drop,
free domain for the first year, 14-day trial. Explicitly aimed at non-technical
users.
**Unverified:** storage limits are not published on the builder page, and the
long commitment is how the headline price is reached. Check both.

### 6. Webnode — the original candidate, no longer preferred
Workable but beaten on every axis. **Cannot import HTML, no FTP, no source
access, and no CSS editing** — everything is rebuilt by hand in their editor.
Free tier restricts file types; premium caps a file at 400 MB. Per-plan storage
is not published anywhere retrievable.

### 7. Squarespace — back in play, loses on language
The most polished output of the three main contenders. It was previously ruled
out on its **20 MB file cap**, which no longer matters now the scores are in
Drive. It loses on Turkish: available as an *account* language only, and
"slowly introducing", with parts of the platform untranslated.
Note: **Square** (which owns Weebly and is closing it) and **Squarespace** are
unrelated companies. Moving there would not mean returning to the same vendor.

### Summary

| Platform | Site editing | Big/odd files | Members area | Cost |
|---|---|---|---|---|
| Platform | Editing | Turkish | Maintenance | Cost |
|---|---|---|---|---|
| **Wix** | Closest to Weebly | Full UI + phone support | None | Paid |
| **Google Sites** | Simplest, plainest | Full | None | Free |
| **Squarespace** | Most polished | Account only, partial | None | Paid |
| **Jimdo** | Simple | Unverified | None | Paid |
| **Hostinger** | Simple | Unverified | None | From $2.99/mo |
| **Webnode** | Manual rebuild | Yes | None | Paid |
| **WordPress** | Capable | Yes | **Ongoing — excluded** | $4–25/mo |

**Recommended: Wix**, because it is the nearest thing to the tool the choir
already knew, so nobody retrains, and its Turkish support is complete including
phone support. **Google Sites** is the credible free alternative: the form is a
Google Form and the files are in Drive, so it is the only option where the
committee learns one ecosystem instead of three — at the cost of a plainer look.

Rebuilding is not a factor in the choice. Ten pages can be built on any of these
platforms through the browser.

Sources:
- https://support.wix.com/en/article/about-storage-and-bandwidth
- https://support.wix.com/en/article/wix-editor-creating-members-only-pages
- https://support.wix.com/en/article/languages-available-in-wix
- https://wordpress.com/pricing/
- https://support.squarespace.com/hc/en-us/articles/205813928-Uploading-and-managing-files
- https://www.webnode.com/support/editor-and-content-faq/
- https://support.google.com/nonprofits/answer/3215869
- https://help.jimdo.com/hc/en-us/articles/40688752248212
- https://www.hostinger.com/website-builder

---

## 6. Decisions needed

**6.1 — Where does the rehearsal library live?**
Recommended: Google Drive. Free via Google Workspace for Nonprofits, which
needs proof of registered charity status in Türkiye. İAK describes itself as
"bağımsız, kâr amacı gütmeyen bir kuruluş", so it may qualify — but nobody has
confirmed whether it is formally registered as a dernek or vakıf. If not, a
paid Google One or Dropbox plan does the same job for a few euros a month and
nothing else about the plan changes.

**6.2 — Where does the website live?**
See section 5. Wix if it should look good and a monthly fee is acceptable.

**6.3 — Do the scores stay behind access control?**
They are published editions: Karl Jenkins, Mozart, Fauré, Dvořák, Mahler. On
Weebly they sat behind a member login. This is a copyright question, not a
technical one. Every recommended option can do either.

**6.4 — Convert the 16 WAVs to MP3?** See section 4. 828 MB → roughly 70 MB.

**6.5 — Repack the 31 `.rar` files as `.zip`?** See section 4. Removes the
file type most likely to be rejected.

**6.6 — Does the A–U/V glossary stay as 20 pages?**
It is a Turkish–English music terminology glossary spread over 20 pages of 11
to 198 words each. It would work better as one page.

---

## 7. Two things to be careful with

**The 877 email addresses never opted in to marketing.** They are in
`applicant-emails.csv`, sourced from Weebly Promote, which had copied
membership-form and contact-form entrants into a mailing group. No names, no
consent record. Treat as a contact list for re-establishing touch, not a
mailing list. Turkish KVKK applies, and GDPR for any EU-resident members.

**The domain is safe and is not with Weebly.** `istanbulavrupakorosu.org` is at
GoDaddy, paid through **31 July 2028**, auto-renew on, GoDaddy nameservers and
GoDaddy email. Weebly's shutdown cannot take it. The one real risk is losing
access to the GoDaddy account — if a former board member set it up, chase that
now, because GoDaddy account recovery is slow.

---

## 8. What is in this package

```
HANDOVER-ANALYSIS-v3.docx this document — open with Google Docs or Word
HANDOVER-ANALYSIS-v3.md   the same document in plain text
applicant-emails.csv      877 addresses (see section 7)
missing-files.txt         51 files that no longer exist anywhere
media-manifest.json       every media file: size, hash, alternate names

rebuild/                  one file per page, in build order
  00-BUILD-ORDER.md       start here: nav tree, nesting, where the work is
  NN-<page>.md            title, parent, SEO fields, text to paste, files to upload
  index.json              same data as JSON

content/                  the 44 pages as plain text, navigation stripped

site-structure/           Weebly's own page hierarchy and theme CSS
  pages_333433648576017344.json   authoritative page list with nesting
  theme_*.css                     the real site theme
```

**Not included — the 593 media files, 1.88 GB.** They do not compress (97 MB
of WAV gzips to 91 MB), so zipping achieves nothing. Share that folder through
Drive or WeTransfer. Michael has it at
`~/Downloads/istanbulavrupakorosu-recovery/webnode/media/`.

**Also not included — a working offline copy of the old site**, 46 pages with
styling and images intact, at `.../archive/index.html`. Useful as a visual
reference and a permanent record; not needed for the decisions above.

---

## 9. Suggested order

1. Confirm access to the GoDaddy account — this gates everything
2. Decide 6.1 and 6.2, the two platform questions
3. If going the Google route, apply for Google for Nonprofits early
4. Do 6.4 and 6.5 — they shrink the library to roughly 600 MB
5. Upload the library, set sharing rules (6.3)
6. Rebuild pages from `rebuild/00-BUILD-ORDER.md`, largest first
7. Point the domain at the new site — one A record change at GoDaddy
