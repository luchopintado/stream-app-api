---
description: Migrate project from Yarn to PNPM
---

## Overview
This workflow guides you through replacing Yarn with PNPM as the package manager for the **stream-app-api** project. It removes the existing `yarn.lock`, installs PNPM (if not already installed), generates a `pnpm-lock.yaml`, and updates any Yarn‑specific scripts.

## Steps
1. **Install PNPM globally (if needed)**
   ```bash
   npm i -g pnpm
   ```
   // turbo
2. **Remove Yarn lock file**
   ```bash
   rm -f yarn.lock
   ```
   // turbo
3. **Install dependencies with PNPM**
   ```bash
   pnpm install
   ```
   // turbo
4. **Update package.json scripts (if they reference Yarn)**
   - Open `package.json`.
   - Replace any `yarn` commands with the equivalent `pnpm` commands (e.g., `yarn run` → `pnpm run`).
   - Save the file.
5. **Verify the setup**
   ```bash
   pnpm test   # or any existing test script
   pnpm start  # ensure the app runs as expected
   ```
   // turbo
6. **Commit the changes**
   ```bash
   git add .
   git commit -m "Migrate from Yarn to PNPM"
   ```
   // turbo

## Notes
- PNPM creates a `pnpm-lock.yaml` file which replaces `yarn.lock`.
- If you use a CI pipeline, ensure it runs `pnpm install` instead of `yarn install`.
- For monorepos, consider adding a `pnpm-workspace.yaml` file.
