# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML fan site for Bugatti (Veyron 16.4), built as a frontend practice project. No build system, package manager, or server — open HTML files directly in a browser.

## Page Structure & Navigation Flow

Three pages with a deliberate entry flow:

1. `index.html` — Splash/landing page. Animated car image with headlamp fade-in effect, background audio via jPlayer, and language selector buttons (both currently navigate to `home.html`; `home_en.html` does not exist).
2. `home.html` — Main homepage. Bootstrap navbar, banner with video modal (video loaded from external OSS URL), image grid of car models, and footer with social links.
3. `prodact.html` — Product detail page. Full-page panel sections (Mission, Gallery, Technical details, Technology, Contact) with a fixed side navigation. Uses a custom panel/section scroll layout driven by `demo.css` and `style2.css`.

## JS Architecture

- `myJs.js` — Controls `index.html`: jPlayer audio autoplay (2s delay), lamp opacity animations via jQuery `.animate()`, and fade-out transitions on language link clicks.
- `sectionjs.js` — Controls `home.html`: navbar background toggle on scroll, play button centering.
- `prodact.html` has inline scripts for BlackBox modal (disclaimer popup and close).

## CSS Layers

Each page loads a specific subset of stylesheets — they are not shared globally:

| File | Used by |
|---|---|
| `style/myApp.css` | All pages (shared base styles) |
| `style/bootstrap.min.css` | All pages |
| `style/blackbox.css` | `home.html`, `prodact.html` |
| `style/animate.min.css` | `index.html` only |
| `style/demo.css` | `prodact.html` only |
| `style/style2.css` | `prodact.html` only |

## Third-Party Libraries (all vendored locally)

- jQuery 3.0.0
- Bootstrap 3 (CSS + JS)
- jPlayer — audio playback on `index.html`
- BlackBox — modal/alert overlay used on `home.html` and `prodact.html`
- WOW.js — scroll-triggered CSS animations (`animate.min.css`) on `index.html`

## Known Issues

- `home_en.html` is referenced in `myJs.js` but does not exist — the English language link will 404.
- The video in `home.html` loads from an external Alibaba OSS URL (`mangguoaidami.oss-cn-shanghai.aliyuncs.com`) which may be unavailable.
- Both language buttons in `index.html` navigate to `home.html` (the English redirect is overridden by a duplicate event listener).
