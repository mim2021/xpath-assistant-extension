# XPath Assistant

A Chrome DevTools extension that helps test automation engineers inspect web elements, generate XPath/CSS selectors, and build [ZeuZ](https://zeuz.ai) test steps directly from the browser.

In Chrome DevTools, the extension appears as a panel named **QA Assistant**.

## Background

A full UI redesign of a client's web portal invalidated the locators in a set of automated test cases two days before a release. Finding and validating replacements by hand was not realistic in the time left. I built the first version of this extension in one day: click an element, check whether its locator is unique, and copy a ready-to-use ZeuZ step. The automation team used it to update most of the broken locators and deliver the release on schedule. I have continued to improve it since.

## Features

- **Capture mode:** inspect a single element and see its details and selectors.
- **Record mode:** log a sequence of user actions (clicks, text entry and more) as steps.
- **Selector details for each step:** recommended XPath, relative XPath, absolute XPath and CSS selector.
- **Live match count:** shows how many elements a locator matches and flags locators that are not unique.
- **Element state:** visible, enabled, checked and selected.
- **ZeuZ step output:** each element becomes a ZeuZ step in its human-readable format (locator parameters plus an action).
- **Editable actions:** choose the action for each step (click, enter text, wait and more), or use the generated step as it is.
- **Copy and export:** copy a single step, a selection or all steps, or export them.

## Known limitations and work in progress

- **Confidence score:** a confidence percentage is shown for the recommended selector, but the scoring logic is still being refined. Treat it as a rough guide.
- **Freeze Page:** not working as expected yet.
- Output is designed for ZeuZ's step format. Other frameworks are not supported.
- The extension was built and tested mainly on the web application described above, so behaviour on other sites may vary.

## Installation

A ready-to-use build is included in `dist/`.

1. Open `chrome://extensions/`
2. Turn on **Developer mode**
3. Click **Load unpacked**
4. Select the `dist/` folder
5. Open any web page, press F12, and select the **QA Assistant** panel

## Development

```bash
npm install
npm run dev          # build in watch mode
npm run build        # production build
npm run type-check   # TypeScript check
npm test             # run Vitest tests
```

## Tech stack

TypeScript · React · Chrome Extension API · Zustand · Webpack · Tailwind CSS · Vitest

## Project structure

```
src/       Source code
public/    Extension manifest and assets
dist/      Ready-to-test build
.kiro/     Requirements and design documentation
```

## Development approach

Built with an AI-assisted, spec-driven workflow ([Kiro](https://kiro.dev)). The requirements and design documents are in `.kiro/`. I defined the requirements, directed the implementation and tested the tool in a live project.

## Roadmap

- Improve the selector confidence score
- Fix Freeze Page
- Add more automated tests
- Support more output formats

## License

MIT
