# Gilbert Webdesign - Agent Context

## Projektübersicht

**Gilbert Webdesign** ist eine professionelle Marketing-/Portfolio-Website für eine freiberufliche Webdesign-Agentur. Die Website richtet sich an B2B-Kunden im Gesundheits- und Wellness-Bereich (Arztpraxen, Physiotherapie, Wellness-Studios) in Berlin.

**Inhaber:** Laurenz Gilbert
**Domain:** lcg-webdesign.de
**Kontakt:** kontakt@lcg-webdesign.de

---

## Tech Stack

| Technologie | Version | Verwendung |
|-------------|---------|------------|
| Astro | 5.17.3 | Static Site Generator (Hauptframework) |
| React | 19.2.4 | Interaktive UI-Komponenten |
| Tailwind CSS | 3.4.19 | Styling |
| Lucide React | 0.575.0 | Icons |
| TypeScript | - | ES Module Konfiguration |

### Deployment
- **Hosting:** Cloudflare Pages
- **CI/CD:** GitHub Actions (`.github/workflows/cloudflare-pages.yml`)
- **Build:** `npm run build` → `/dist`

---

## Projektstruktur

```
Gilbert Webdesign/
├── src/
│   ├── pages/                    # Astro-Seiten (file-based routing)
│   │   ├── index.astro          # Homepage (lädt App.jsx)
│   │   ├── impressum.astro      # Impressum
│   │   ├── datenschutz.astro    # Datenschutzerklärung
│   │   └── agb.astro            # AGB
│   │
│   ├── components/               # React-Komponenten für Unterseiten
│   │   ├── ImpressumPage.jsx
│   │   ├── DatenschutzPage.jsx
│   │   └── AGBPage.jsx
│   │
│   └── styles/
│       └── global.css           # Tailwind-Direktiven
│
├── public/                       # Statische Assets
│   ├── robots.txt
│   ├── sitemap.xml
│   └── *.webp                   # Bilder
│
├── App.jsx                       # Haupt-React-Komponente (Homepage)
│
├── *.txt                         # Rechtliche Texte (Quelle)
│   ├── AGB.txt
│   ├── Datenschutzerklärung.txt
│   └── Impressum.txt
│
└── Config-Dateien
    ├── package.json
    ├── astro.config.mjs
    └── tailwind.config.mjs
```

---

## Wichtige Dateien

### App.jsx (Hauptdatei)
Die zentrale React-Komponente enthält die komplette Homepage mit:
- **Navigation** - Fixed Header, Mobile Hamburger-Menü
- **Hero Section** - Hauptüberschrift, CTAs
- **Philosophie** - 6 Feature-Cards
- **Referenzen** - Case Study mit AutoScrollMockup
- **Über mich** - Biografie, Werdegang
- **Leistungen** - Preiskarten (€1.290 / €2.290)
- **FAQ** - Accordion-Komponente
- **Footer/Kontakt** - CTA, Kontaktdaten, rechtliche Links

### Wichtige Komponenten in App.jsx
- `Reveal` - Scroll-Animation mit Intersection Observer
- `AutoScrollMockup` - iPhone-Mockup mit Auto-Scroll
- `FAQItem` - Accordion für FAQ-Bereich

---

## Seiten & Routing

| Route | Datei | Beschreibung |
|-------|-------|--------------|
| `/` | `index.astro` → `App.jsx` | Homepage (One-Pager) |
| `/impressum` | `impressum.astro` | Impressum |
| `/datenschutz` | `datenschutz.astro` | Datenschutzerklärung |
| `/agb` | `agb.astro` | AGB |

---

## Preismodell

### Hauptpakete
1. **Digitale Visitenkarte** (One-Pager): €1.290 netto
2. **Umfassende Praxis-Website** (Multi-Pager): €2.290 netto

### Wartungspaket (optional)
- **Technischer Support:** €59/Monat (Fokus auf Support, CMS-Hilfe und kleine Anpassungen, *kein* Hosting/DSGVO-Schutz inkludiert)

---

## Commands

```bash
npm run dev       # Entwicklungsserver starten
npm run build     # Produktions-Build erstellen
npm run preview   # Build lokal testen
```

---

## Deployment-Workflow

1. Push auf `main` Branch
2. GitHub Action wird getriggert
3. Build mit Node.js 20
4. Deploy auf Cloudflare Pages via Wrangler

**Secrets erforderlich:**
- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID`

---

## SEO & Performance

- **Lighthouse Scores:** 100/100 Performance, 100/100 Best Practices, 95/100 Accessibility, 100/100 SEO
- Strukturierte Daten (JSON-LD): WebSite, Organization, LocalBusiness
- Sitemap.xml mit 4 URLs
- robots.txt konfiguriert
- WebP-Bilder für optimale Ladezeiten

---

## Stilrichtlinien & Design-System

Das Design ist konsequent auf eine seriöse B2B-Zielgruppe (Praxen, Therapeuten, Studios) ausgerichtet. Es wirkt modern, aufgeräumt, minimalistisch und vertrauenserweckend.

- **Farbpalette:** 
  - Hauptsächlich monochrome Slate-Töne (`bg-slate-50` oder `bg-white` für Hintergründe, `text-slate-900` für primäre Texte/Überschriften, `text-slate-600` oder `text-slate-500` für Fließtexte).
  - Akzentfarbe ist ein tiefes, seriöses Blau (`blue-900` für primäre Buttons, Links und Icons, `bg-blue-50` für Icon-Hintergründe). Gelegentlich wird `blue-600` für besondere Highlights (z.B. das Premium-Preispaket) verwendet.
- **Typografie:** 
  - Überschriften nutzen `font-serif` (wirkt klassisch, hochwertig und vertrauenswürdig).
  - Fließtext nutzt `font-sans` (System-Fonts für optimale Lesbarkeit und moderne Anmutung).
- **Formensprache & Layout:** 
  - Dezent abgerundete Ecken (`rounded-sm` statt großer Rundungen) für einen klaren, professionellen Look.
  - Großzügiger Weißraum / Padding (z.B. `py-24` für Sections, `gap-8` oder `gap-16` für Grids).
  - Subtile Abgrenzungen durch feine Ränder (`border-slate-100` oder `border-slate-200`) und sanfte Schatten (`shadow-sm`, oder `shadow-xl shadow-slate-200/50` für besondere Elemente).
- **Animationen & Interaktionen:** 
  - Dezente Scroll-Reveal-Effekte über die Custom-Komponente `Reveal` (Elemente faden weich ein und sliden leicht nach oben oder zur Seite).
  - Hover-Effekte sind subtil und wertig (z.B. leichte Skalierung von Icons `group-hover:scale-110`, Farbwechsel bei Texten/Buttons).
  - Transparente, fixierte Hauptnavigation mit Blur-Effekt (`bg-white/80 backdrop-blur-md`).
- **Icons & Medien:** 
  - Einheitliche Verwendung von `lucide-react` (oft mit `size={24}` oder `size={28}`).
  - Bilder im WebP-Format, oft dezent eingefasst oder mit sanften Hintergrund-Blobs (`blur-3xl`) kombiniert. Keine verspielten Illustrationen oder Emojis.


---

## Hinweise für Agents

1. **Hauptarbeit findet in `App.jsx` statt** - hier ist die gesamte Homepage-Logik
2. **Rechtliche Seiten** haben ihre Inhalte in `.txt`-Dateien im Root
3. **Bilder** gehören in `/public` als WebP
4. **Keine Emojis** verwenden (professioneller B2B-Kontext)
5. **Deutsche Sprache** - Website und Inhalte sind auf Deutsch
6. **B2B-Fokus** - Alle Preise sind Nettopreise, Zielgruppe sind Unternehmer
