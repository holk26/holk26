# CV – Homero Cabrera Araque

Professional CV built with [Astro](https://astro.build). Canadian format, PDF-ready, data-driven via `cv.json`.

## Project Structure

```
cv/
├── cv.json                  # ← Edit this file to update your CV data
├── src/
│   ├── pages/
│   │   └── index.astro      # Main CV page
│   ├── layouts/
│   │   └── Layout.astro     # HTML shell + global styles
│   └── components/
│       ├── Header.astro
│       ├── Summary.astro
│       ├── Skills.astro
│       ├── Experience.astro
│       ├── Education.astro
│       ├── Certifications.astro
│       └── Languages.astro
├── astro.config.mjs
├── package.json
└── Dockerfile
```

## Quick Start

```bash
# Install dependencies
npm install

# Development server
npm run dev        # http://localhost:4321

# Production build
npm run build      # Output in dist/

# Preview production build
npm run preview
```

## Update Your CV

All content lives in **`cv.json`**. Edit that file to tailor your résumé for any job posting — no component code changes needed.

## Save as PDF

1. Open the page in a browser (`npm run dev` or `npm run preview`).
2. Click **🖨 Print / Save as PDF**.
3. In the print dialog, choose **Save as PDF**, set margins to *None* or *Minimum*, and enable *Background graphics*.

## Docker

```bash
# Build the image
docker build -t cv .

# Run (available at http://localhost:8080)
docker run -p 8080:80 cv
```
