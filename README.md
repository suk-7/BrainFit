# Brain Fit, LLC — Website

Static multi-page website for **Brain Fit, LLC**, a federally registered multi-specialty provider network based in Phoenix, Arizona. The site is aimed at recruiting licensed clinicians (psychologists, dentists, audiologists, optometrists, and physicians) and serves federal/government procurement partners.

---

## Project overview

This is a **pure HTML/CSS/JS** project — no build system, no npm, no framework. Every page is a standalone `.html` file with its own embedded `<style>` block and inline `<script>` at the bottom. There is no shared stylesheet or bundler.

---

## File structure

```
BrainFit/
├── Home.html                       # Landing page — hero, specialties, network model, ecosystem, FAQ, contact form
├── About.html                      # Company story, leadership bios, values, integrated network
├── Veterans_CP.html                # Veterans & C&P page — recruits clinicians for federal evaluation work
├── Contracting.html                # Capability statement — federal contracting, NAICS codes, credentials
├── Partner_and_Network.html        # Provider network overview — 21 credentialed providers, 10 states
├── Contact.html                    # Routed contact page (4 audience paths), contact form, map embed
└── BrainFit_Capability_Statement.pdf  # Downloadable PDF capability statement
```

---

## Running locally

No install required. Serve the folder with any static file server.

**Python (recommended):**

```bash
cd BrainFit
python3 -m http.server 8080
```

Then open [http://localhost:8080/Home.html](http://localhost:8080/Home.html) in your browser.

**VS Code Live Server extension** also works — right-click any `.html` file → _Open with Live Server_.

---

## Pages

| Page             | URL                         | Purpose                                                                                                                                                      |
| ---------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Home             | `/Home.html`                | Primary landing — hero, specialties tab panel, network model flow diagram, ecosystem SVG diagram, affiliate cards, coverage map, FAQ accordion, contact form |
| About            | `/About.html`               | Company story, leadership (Dr. Shelton & Dr. Nguyen), values, integrated network (Brain Fit / Trinity Tree / Desert Recovery Centers), FAQ                   |
| Veterans & C&P   | `/Veterans_CP.html`         | Recruits clinicians specifically for Compensation & Pension federal evaluation work; includes specialty cards, onboarding steps, FAQ, and application form   |
| Contracting      | `/Contracting.html`         | Federal capability statement — NAICS codes, differentiators, core competencies, provider network stats, contract vehicles (SAM.gov, HIPAA, 42 CFR Part 2)    |
| Provider Network | `/Partner_and_Network.html` | Network overview — 21 credentialed providers across 10 states                                                                                                |
| Contact          | `/Contact.html`             | Routed contact page with 4 audience paths (procurement partners, clinicians, health systems, patients/families) and a contact form                           |

---

## Forms & backend

Both the **Veterans_CP** application form and the **Contact** page form submit data to a **Google Apps Script** endpoint that writes entries into a Google Sheet.

**Endpoint:**

```
https://script.google.com/macros/s/AKfycbzOIdkTTMBifbDvpjFvjr-M_bLlPRaRfPFc5blPVqhW6t2gc70_XreaBD-dndgdG-vr8Q/exec
```

Each form POST sends a JSON body with a `sheet` field (e.g. `"Veterans_CP"`) that tells the script which Google Sheet tab to write to, plus form field values. Requests use `mode: "no-cors"`.

---

## Design system

Each page has its own CSS custom properties (`:root` block) but they all share the same visual language:

| Token              | Value                 | Usage                                          |
| ------------------ | --------------------- | ---------------------------------------------- |
| Pine / Navy (dark) | `#0e5560`             | Nav background, hero background, dark sections |
| Pine / Navy (mid)  | `#176674` – `#2d8898` | Section accents, stat numbers, borders         |
| Brass / Bronze     | `#b8794a`             | CTA buttons, badge dots, bullet accents        |
| Cream              | `#fbf8f1`             | Light section backgrounds, submit buttons      |
| Cream edge         | `#e0cd8a`             | Borders on cream sections                      |

**Typography:**

- Headings: `DM Serif Display` (Google Fonts)
- Body: `DM Sans` (Google Fonts)

---

## Key interactions

- **Scroll progress bar** — fixed top bar showing page scroll position
- **Nav shrink on scroll** — nav compresses and blurs on scroll past 30px
- **Scroll-reveal animations** — cards and sections fade/slide up via IntersectionObserver
- **Animated stat counters** — numbers count up when scrolled into view
- **FAQ accordions** — collapsible Q&A powered by vanilla JS
- **Back-to-top button** — appears after scrolling 600px
- **Button ripple effect** — click ripple on all CTAs

---

## Branch structure

| Branch | Purpose                                               |
| ------ | ----------------------------------------------------- |
| `dev`  | Active development branch — all changes go here first |
| `main` | Production / stable                                   |

Always branch off `dev` for new features. Open a PR from your feature branch into `dev`, not into `main`.

---

## Recent changes

| Date       | Change                                                                                                                                |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 2026-06-02 | Removed hero grid overlay (`::before` CSS) from `Home.html` and `About.html` to match the clean hero background on `Veterans_CP.html` |
| Earlier    | Google Sheets backend wired up for Contact and Veterans_CP forms                                                                      |
| Earlier    | Added Contracting, Partner_and_Network, and Contact pages; removed standalone Ecosystem page                                          |

---

## Contact

**Dr. Jonathan Shelton** — Co-Owner & Managing Director  
jshelton@brainfitteam.com · (623) 688-8598 · www.brainfitteam.com
