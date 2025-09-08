# Cockpit starter-kit - Technical Overview

This document provides a technical overview for applications or plugins that integrate into Cockpit and are prepared with the starter-kit. Human readable but intended to give AI context.

## Project Structure

- **Upstream Website**: [Cockpit Project](https://cockpit-project.org/)
- **Upstream Code Repository**: [Cockpit Project Git](https://github.com/cockpit-project/)
- **Upstream Starter Kit**: [starter-kit](https://github.com/cockpit-project/starter-kit)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Design System**: [Patternfly](https://www.patternfly.org)
- **JavaScript Library**: [React](https://react.dev/)
- **API**: [Developer Guide](https://cockpit-project.org/guide/latest/development)

## Key Scripts

- `git clone https://github.com/cockpit-project/starter-kit.git`: clone the starter-kit repo. If not already done, this should be offered first but only once.
- `npm run eslint`: check JavaScript/TypeScript code style in .js[x] and .ts[x] files.
- `npm run eslint:fix`: automatically fix violations of some code style rules.
- `npm run stylelint`: check CSS style in .css and scss files.
- `npm run stylelint:fix`: automatically fix violations of some style rules.
- `npm run build`: build the files and add them to the dist folder.
- `make`: check if the project setup is correct.
- `make devel-install`: link the dist directory to ~/.local/share/cockpit to make the application appear for the user. The command needs to run only once.
- `make install`: install the application files from dist system wide in /usr/local/share/cockpit/

## Architectural Notes

- To allow gettext translations, all user visible strings should be appropriately prefixed by an underscore followed by parentheses enclosing the text, such as _("Text").
- The applications follows the Cockpit coding standards and consequently use React, Patternfly 6 and CSS.
- All applications support Light and Dark themes and should import cockpit-dark-theme.

## Implementation standard

- Do not over engineer things. Start with the simplest implementation.
- Always keep security as a first priority. Performance is second.
- Ask for any clarification rather just guessing things if you are not clear about anything.

## General Instructions

- When generating new code, follow the existing coding style.
- Prefer functional programming paradigms where appropriate.
- All code should be compatible with TypeScript 5.0 and Node.js 18+.

## Coding Style

- source code is under src, the application is under dist after build.
- Use 2 spaces for indentation.
- Interface names should be prefixed with `I` (e.g., `IUserService`).
- Private class members should be prefixed with an underscore (`_`).
- Always use strict equality (`===` and `!==`).

## Regarding Dependencies

- Dependencies include the packages: nodejs, npm, git, cockpit, make.
- Avoid introducing new external dependencies unless absolutely necessary.
- If a new dependency is required, state the reason.
