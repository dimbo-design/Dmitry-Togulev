# Dmitry Togulev / Дмитрий Тогулев — CV / Portfolio

> Personal CV & portfolio site · Senior Product Designer · ex-Uzum · ex-KazanExpress <br>
> Личный сайт-портфолио и резюме · Старший продуктовый дизайнер

🔗 **Live site · Сайт**: [dimbo-design.github.io/Dmitry-Togulev](https://dimbo-design.github.io/Dmitry-Togulev/) <br>
📄 **PDF resume · PDF-резюме**: [download · скачать](https://dimbo-design.github.io/Dmitry-Togulev/assets/Product_Design_Dmitry_Togulev.pdf)

---

## About the site

Old-school static site — pure HTML/CSS + minimal vanilla JS. No frameworks, no build step.

Page covers:
- Hero with positioning
- Portfolio in four collapsible groups, 11 cases: Teams & Clients (warehouse case KazanExpress × Uzum, Nodari Appolonov, Spendora), Experiments (Lapka, Heavy CV), Tabletop RPG (Myth List, Dungeon World rulebook, Myth Radio), Board Games (Release at any cost in print and on the web, one more board game)
- A collapsed group shows previews of its cases: on hover with a mouse, always on touch screens
- Case rows: media on the left, text on the right, the shorter column sticks to the longer one
- MythHand and Habr articles cards
- Experience timeline (10+ years)
- Contacts with copy-to-clipboard email and PDF download

## Stack

- **HTML5 / CSS** — all styles in single `<style>` block inside `index.html`
- **Vanilla JS** — clipboard copy, right header that compacts on scroll, collapsible case groups with previews, case media slider with a fullscreen gallery (rotate for wide frames on phones), warehouse case accordion
- **Font**: Fixel Display (OTF, weights 400–700)
- **No build, no dependencies**
- **Hosted on GitHub Pages**

## Files

- `index.html` — main page (HTML + CSS + JS in one file)
- `assets/` — images, videos, downloadable PDF
- `fonts/` — Fixel Display OTF files

## Notes

- Single-file architecture by choice — portability + zero ceremony.
- The site shows the projects; the PDF is the resume.

---

Designer-led, vibecoded with [Claude Code](https://claude.com/claude-code). I'm a product designer who coordinates the build through AI rather than writing every line by hand — this site is part of that practice.
