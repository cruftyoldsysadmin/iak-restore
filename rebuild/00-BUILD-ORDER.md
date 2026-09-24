# İstanbul Avrupa Korosu — rebuild pack

One file per page: title, navigation position, SEO fields, text to paste, images
to upload. Structure comes from Weebly's own page data, so nesting and SEO fields
match the real site.

## Scope

**Build the core pages now.** Rehearsal audio, scores and practice files are in
Google Drive, shared with the choir — they are not part of the website.

**The application form is a Google Form**, embedded in the Üye Başvuru page, with
responses landing in a Sheet the choir owns. This is deliberate: 1,666 old
applications were lost because Weebly held them and stripped them on export. A
Google Form cannot fail that way, and it stays portable if the site moves again.

## Core build — 10 pages, 5170 words

| # | Page | Words | Images | Notes |
|---|------|------:|------:|-------|
| 1 | Ana Sayfa | 44 | 1 |  |
| 2 | Hakkinda | 2370 | 1 |  |
| 3 | Galeri | 10 | 16 |  |
| 4 | Etkinlikler | 780 | 21 |  |
| 5 | Üye Başvuru | 57 | 0 | **embed the Google Form here** |
| 6 | İletişim | 15 | 0 |  |
| 7 | Sponsor | 5 | 3 | hidden from nav |
| 8 | Events | 728 | 17 | hidden from nav; English version |
| 9 | Gallery | 10 | 16 | hidden from nav; English version |
| 10 | Müzik Terimleri | 1151 | 0 | **replaces 17 letter pages** |

Two pages carry most of the text: **Hakkında** (2,370 words) and **Etkinlikler**
(780). Everything else is short.

## Repertoire pages — 5, decide separately

These look like content pages but are really file lists. Their links point at
material that now lives in Drive, so rebuild them only if you want public pages
that link out to Drive folders.

| Page | Words | Files it linked |
|---|------:|---|
| Christmas Carols | 649 | 61 MIDI |
| Mahler - Symphony 2 | 22 | 1 PDF |
| Dvorak - Stabat Mater | 103 | 3 PDF |
| Rossini | 8 | 1 file |
| Zelenka Bach Byrd | 224 | 20 MP3 |

## The glossary

17 per-letter pages are combined into one **Müzik Terimleri** page — 141 terms with
definitions, 104 without, 245 total. This fixes a real fault: on the old site terms
and definitions were two separate side-by-side blocks, so from `Allegro` onward every
definition displayed against the wrong term. Letters **C** and **F** need a musician
to spot-check the pairing — flagged in the page file. Originals kept in
`superseded-letter-pages/`, structured data in `../../glossary.json`.

## Out of scope — member section (11 pages)

Not being rebuilt. This content is in Google Drive.

- Üye Girişi
- Materyaller
- Jenkins Motets
- Prova Planı / Rehearsal Plan
- FAURE
- Members
- Handel
- Mozart Requiem
- Daphnis et Chloe
- Biz Kimiz
- Biz Kimiz
