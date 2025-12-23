# AGENTS.md

> **Mission:** You are an expert TypeScript/React engineer building a module for the Cockpit Project. Your code must be secure, performant, and strictly adhere to Patternfly 6 design system standards.

## 1. Context & Architecture

### Tech Stack
- **Runtime:** Node.js 18+
- **Language:** TypeScript 5.0+
- **Framework:** React (Functional components, Hooks only).
- **UI System:** Patternfly 6.
- **Build System:** Custom `build.js` / Makefile wrapper around ESBuild/Webpack.

### Directory Structure & Artifacts
- `/src`: Source code (TypeScript/React).
- `/dist`: Compiled build artifacts.
- `/test`: Integration tests (Python/Chrome DevTools Protocol).
- `~/.local/share/cockpit/`: Local development install path (symlinked via `make devel-install`).

## 2. Operational Toolbelt

### Build & Install
- **Initial Setup:** `make` (runs build and checks setup).
- **Build:** `npm run build` (populates `/dist`).
- **Dev Install:** `make devel-install` (links `/dist` to Cockpit user directory).
- **System Install:** `sudo make install` (installs system-wide to `/usr/local/share/cockpit/`).

### Watch & Remote Development
- **Local Watch:** `./build.js -w` or `make watch` (rebuilds on change).
- **Remote VM Watch:** `RSYNC=user@hostname make watch` (syncs changes to a remote VM).
- **Remote User Watch:** `RSYNC_DEVEL=user@hostname make watch` (syncs to `~/.local` on remote).

### Testing & Quality
- **Static Analysis:** `npm run eslint` and `npm run stylelint`.
- **Fix Formatting:** `npm run eslint:fix` and `npm run stylelint:fix`.
- **Integration Tests:** `make check` (Builds RPM, runs tests in VM).
- **Test Options:** `TEST_OS=centos-9-stream make check` (Select OS).

## 3. Coding Standards

### Implementation Rules
- **Equality:** Always use strict equality (`===` and `!==`).
- **Localization:** All user-visible strings must be wrapped in `_("Text")` for gettext support.

### UI & Styling
- **Patternfly First:** Use official Patternfly React components. Do not invent custom CSS unless absolutely necessary.
- **Theming:** Support both Light and Dark modes. Import `cockpit-dark-theme` where required.

## 4. Dependencies & Security
- **Restricted:** Do not add new NPM dependencies without explicit user request.
- **Allowed:** `nodejs`, `npm`, `git`, `cockpit`, `make`.
- **Security:** Prioritize security over performance. Validate all inputs.

## 5. Anti-Patterns (DO NOT DO)
- ❌ Do not use `any`.
- ❌ Do not modify files in `dist/` or `pkg/`.
- ❌ Do not write Class Components (use React Hooks).
- ❌ Do not hardcode English strings without the `_()` wrapper.
