# library-api

A sample setup for running Postman collections with Newman in a GitHub Actions pipeline.

---

## Overview

This repo shows how to run API tests automatically on every commit. It version-controls a Postman collection, runs it through Newman on push, and publishes the HTML report to GitHub Pages so results are easy to share.

---

## How It Works

The workflow triggers on any push or pull request to `main` that touches the collection files or workflow config. It installs Newman, runs the collection, and produces three outputs: an HTML report, a JUnit XML file for CI integration, and a badge JSON file for the status badge.

Test duration is tracked across runs in a `history.json` file and visualized in a `trend.html` page using Chart.js.

---

## Running Locally

```bash
npm install -g newman newman-reporter-htmlextra

newman run "postman/collection.json" \
  -r htmlextra --reporter-htmlextra-export ./report.html
```

---

## Reports

Each run produces:

- `report.html` — full HTML dashboard
- `results.xml` — JUnit format for CI platforms
- `trend.html` — duration trend chart across runs
