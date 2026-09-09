# cv.chaot.dev

<div align="center">

[![Website](https://img.shields.io/badge/website-cv.chaot.dev-20B2AA?style=for-the-badge&logo=googlechrome&logoColor=white)](https://cv.chaot.dev)
[![PDF Resume](https://img.shields.io/badge/download-PDF%20Resume-E53935?style=for-the-badge&logo=adobeacrobatreader&logoColor=white)](https://cv.chaot.dev/cv_en.pdf)
[![GitHub Pages](https://img.shields.io/github/deployments/chaot-dev/cv.chaot.dev/github-pages?label=GitHub%20Pages&style=for-the-badge&logo=github)](https://github.com/chaot-dev/cv.chaot.dev/deployments/activity_log?environment=github-pages)
[![PDF Build](https://img.shields.io/github/actions/workflow/status/chaot-dev/cv.chaot.dev/create_pdf.yml?branch=gh-pages&label=PDF%20Generation&style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/chaot-dev/cv.chaot.dev/actions/workflows/create_pdf.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE.txt)

<p align="center">
  A clean, modern, and responsive online CV & resume website powered by <strong>Jekyll</strong> and <strong>GitHub Pages</strong>, delivered globally via <strong>Cloudflare CDN</strong> with automated PDF generation.
</p>

[**View Live Site »**](https://cv.chaot.dev) · [**Download PDF »**](https://cv.chaot.dev/cv_en.pdf)

</div>

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Project Structure](#project-structure)
- [Quick Start & Local Development](#quick-start--local-development)
  - [Option A: Docker Compose (Recommended)](#option-a-docker-compose-recommended)
  - [Option B: Native Ruby & Bundler](#option-b-native-ruby--bundler)
- [Configuration & Customization](#configuration--customization)
  - [1. Content Configuration (`_data/data.yml`)](#1-content-configuration-_datadatayml)
  - [2. Site & Theme Settings (`_config.yml`)](#2-site--theme-settings-_configyml)
  - [3. Profile Picture & Assets](#3-profile-picture--assets)
  - [4. Color Skins](#4-color-skins)
- [PDF Generation & Print](#pdf-generation--print)
  - [Automated CI/CD via GitHub Actions](#automated-cicd-via-github-actions)
  - [Interactive Browser PDF / Print](#interactive-browser-pdf--print)
- [Deployment](#deployment)
- [Tech Stack](#tech-stack)
- [Credits & Acknowledgments](#credits--acknowledgments)
- [License](#license)

---

## Overview

This repository hosts the source code for [**cv.chaot.dev**](https://cv.chaot.dev), the personal resume of **Martin Spitz** (SysOps / Infrastructure / Security Engineer).

It is built on top of the **Orbit** theme originally created by [Xiaoying Riley](https://themes.3rdwavemedia.com/), adapted for Jekyll by [sharu725](https://github.com/sharu725/online-cv), and further customized with:

- Dedicated print layout and automated PDF builds
- Modern social contact integrations (Bluesky, Mastodon, LeetCode, CodeWars, HackerRank, etc.)
- Additional CV sections (Certifications, Open Source Contributions, Recommendations)
- Containerized development with Docker Compose

---

## Key Features

- **Decoupled Data Architecture**: All personal data, career history, education, skills, and projects live in a single, human-readable YAML file (`_data/data.yml`). No need to edit HTML templates for updates.
- **Dual PDF Export Options**:
  - **Automated CI/CD PDF Pipeline**: GitHub Actions automatically renders and saves `cv_en.pdf` using ConvertAPI on every push to the `gh-pages` branch.
  - **Client-Side Export**: Dedicated `/print` layout with integrated `html2pdf.js` and browser print dialog.
- **8 Pre-configured Color Skins**: Quickly swap color palettes (`turquoise`, `blue`, `green`, `berry`, `orange`, `ceramic`, `teal`, `oceanstale`) directly in `_config.yml`.
- **Modular Sections**:
  - Career Profile & Summary
  - Work Experience & Employment History
  - Education (pluggable into sidebar or main column)
  - Certifications & Credentials
  - Personal Projects & Open Source Contributions
  - Skills & Toolset (with visual proficiency meters)
  - Recommendations & Endorsements
  - Languages & Personal Interests
- **Comprehensive Social & Contact Matrix**: Built-in support for Email, Phone, Timezone, Telegram, Website, LinkedIn, XING, GitHub, GitLab, Bitbucket, Bluesky, Mastodon, Stack Overflow, CodeWars, HackerRank, LeetCode, and Goodreads.
- **Responsive & Mobile Optimized**: Clean presentation across desktops, tablets, and smartphones, with custom Chrome mobile address bar theming.
- **Cloudflare & GitHub Pages Ready**: Seamlessly deploys on GitHub Pages with custom CNAME and Cloudflare CDN caching and security.

---

## Project Structure

```text
cv.chaot.dev/
├── .github/
│   └── workflows/
│       └── create_pdf.yml       # GitHub Actions automated PDF generation
├── _data/
│   └── data.yml                 # Resume content (bio, experiences, skills, links)
├── _includes/                   # Reusable HTML partials
│   ├── career-profile.html      # Profile / Summary section
│   ├── certifications.html     # Certifications section
│   ├── contact.html            # Sidebar contact & social links
│   ├── education.html          # Education history
│   ├── experiences.html        # Work experience list
│   ├── interests.html          # Hobbies & personal interests
│   ├── language.html           # Language proficiencies
│   ├── oss-contributions.html  # Open source contributions
│   ├── projects.html           # Project portfolio
│   ├── recommendations.html    # Testimonials & recommendations
│   ├── sidebar.html            # Sidebar container
│   └── skills.html             # Technical skills and proficiencies
├── _layouts/
│   ├── default.html            # Primary responsive layout
│   └── print.html              # Clean printable layout for PDF generation
├── _sass/
│   ├── _base.scss              # Typography and base styling
│   ├── _print.scss             # Print-specific styling rules
│   ├── _responsive.scss        # Breakpoints and responsive tweaks
│   └── skins/                  # 8 color palette partials
├── assets/
│   ├── css/                    # Compiled stylesheets
│   ├── images/                 # Profile avatars and icons
│   └── js/
│       └── pdf-generator.js    # Client-side html2pdf integration
├── _config.yml                  # Jekyll site settings and theme options
├── docker-compose.yml           # Local development container setup
├── Gemfile                      # Ruby gem dependencies
├── index.html                   # Homepage entry point
└── print.html                   # Print route (/print)
```

---

## Quick Start & Local Development

### Option A: Docker Compose (Recommended)

No local Ruby installation required. Run with Docker Compose:

```bash
# Clone the repository
git clone https://github.com/chaot-dev/cv.chaot.dev.git
cd cv.chaot.dev

# Start Jekyll server with live reloading
docker compose up
```

Open your browser and navigate to:

- **Site:** `http://localhost:4000`
- **Print View:** `http://localhost:4000/print`

---

### Option B: Native Ruby & Bundler

Ensure you have **Ruby** (>= 2.7 or 3.x) and **Bundler** installed.

```bash
# 1. Install dependencies
bundle install

# 2. Start the Jekyll server with live reloading
bundle exec jekyll serve --livereload
```

Open your browser at `http://localhost:4000`.

---

## Configuration & Customization

### 1. Content Configuration (`_data/data.yml`)

All personal details, job experiences, and skill entries are managed in `_data/data.yml`.

```yaml
sidebar:
  name: Your Name
  tagline: Your Title / Specialization
  avatar: profile.png # Put file in assets/images/
  education: True # True = sidebar, False = main section

  # Contact info & social links
  email: user@example.com
  github: username
  linkedin: username
  bluesky: "@handle.bsky.social"
  mastodon: https://instance.social/@user
  pdf: cv_en.pdf # Filename for PDF download button
```

Sections available in `data.yml`:

- `sidebar`: Profile, avatars, social links, languages, interests
- `career-profile`: Professional summary and career statement
- `experiences`: Chronological career history and achievements
- `education`: Academic degrees and professional training
- `certifications`: Industry certifications (LPIC, Microsoft, etc.)
- `projects`: Featured personal and open-source projects
- `skills`: Categorized skill bars with percentage proficiencies

---

### 2. Site & Theme Settings (`_config.yml`)

Configure site-wide metadata and appearance in `_config.yml`:

```yaml
title: Martin Spitz
url: "https://cv.chaot.dev"
description: Martin Spitz - SysOps

# Color Skin Selection
# Options: turquoise, blue, green, berry, orange, ceramic, teal, oceanstale
theme_skin: turquoise

# Chrome mobile status bar color
chrome_mobile_color: "#4CAC9D"

# Build & compression settings
compress-site: yes
```

---

### 3. Profile Picture & Assets

1. Drop your profile image (e.g. `profile.png`, ideally 100x100 square) into `assets/images/`.
2. Reference the filename under `avatar` in `_data/data.yml`.
3. To change the favicon, replace `favicon.ico` in the project root.

---

### 4. Color Skins

You can change the theme color at any time by editing `theme_skin` in `_config.yml`:

| Skin         | Description / Tone                |
| :----------- | :-------------------------------- |
| `turquoise`  | Crisp turquoise teal (default)    |
| `blue`       | Classic professional blue         |
| `green`      | Emerald and mint tones            |
| `berry`      | Modern deep raspberry / berry red |
| `orange`     | Warm amber and vibrant orange     |
| `ceramic`    | Contemporary muted ceramic tones  |
| `teal`       | Deep oceanic teal                 |
| `oceanstale` | Cool slate ocean blue             |

> **Note:** Restart your Jekyll server or Docker container after changing `_config.yml` for skin changes to compile.

---

## PDF Generation & Print

This project provides two distinct methods for generating PDF copies of the resume:

### Automated CI/CD via GitHub Actions

The workflow located in [`.github/workflows/create_pdf.yml`](.github/workflows/create_pdf.yml) automatically executes on pushes to the `gh-pages` branch:

1. Triggers on push to `gh-pages`.
2. Calls the **ConvertAPI** service to convert `http://cv.chaot.dev` into a high-fidelity PDF (`cv_en.pdf`).
3. Uses `stefanzweifel/git-auto-commit-action` to commit the updated `cv_en.pdf` directly back to the `gh-pages` branch.

**Setup Requirement:**

- Add your ConvertAPI secret token to your repository secrets as `CONVERTAPI` (`Settings -> Secrets and variables -> Actions`).

---

### Interactive Browser PDF / Print

Visitors can also export the CV directly from their browser:

- **Print Button**: Opens `/print` in a print-optimized layout with browser-native print dialog (`window.print()`).
- **PDF Button**: Uses `html2pdf.js` to render the CV client-side into an A4 PDF (`<Name>_Resume.pdf`).

---

## Deployment

The site is configured for zero-friction hosting on **GitHub Pages**:

1. **GitHub Pages Source**: Set to deploy from the `gh-pages` branch (root `/`).
2. **Custom Domain**: Set up via the [`CNAME`](CNAME) file (`cv.chaot.dev`).
3. **Cloudflare CDN**: DNS and HTTPS are proxied via Cloudflare for global caching, DDoS protection, and SSL termination.

---

## Tech Stack

- **Static Site Generator:** [Jekyll](https://jekyllrb.com/) 4.x
- **Hosting:** [GitHub Pages](https://pages.github.com/)
- **CDN & DNS:** [Cloudflare](https://www.cloudflare.com/)
- **Styling:** SASS / SCSS & [Bootstrap](https://getbootstrap.com/)
- **Icons:** [Font Awesome 5 / 6](https://fontawesome.com/)
- **PDF Engine (Client):** [html2pdf.js](https://github.com/eKoopmans/html2pdf.js)
- **PDF Engine (CI/CD):** [ConvertAPI](https://www.convertapi.com/)
- **CI/CD Automation:** GitHub Actions

---

## Credits & Acknowledgments

- Design template created by [Xiaoying Riley](https://themes.3rdwavemedia.com/) for developers.
- Jekyll port and architecture inspired by [sharu725/online-cv](https://github.com/sharu725/online-cv).
- Automated commit action by [stefanzweifel/git-auto-commit-action](https://github.com/stefanzweifel/git-auto-commit-action).

---

## License

- Resume content & personal data &copy; Martin Spitz.
- Theme and underlying code are licensed under the [MIT License](LICENSE.txt).
- Design template attribution governed by [Xiaoying Riley's license terms](LICENSE.md).
