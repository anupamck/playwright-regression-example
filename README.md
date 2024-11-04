# Regression Report

## To reproduce:

1. Clone the repository

#### The `apps/playwright` folder is considered the root of the project (default behaviour):

2.  Install dependencies with `pnpm i` (you might need to do this in the apps/playwright folder)
3.  Run one of the example tests by using the UI via the VSCode Playwright Extension

Expected: Due to line 6 of the file playwright.config.ts, the following log should appear in the console: AllYourBaseAreBelongToUs

Actual: Said log appears in the console

#### The monorepo root is considered the root of the project (regression):

2.  Change the playwright version to the latest in the apps/playwright/package.json file
3.  Delete all node_modules folders in the monorepo
4.  Clear the pnpm store with `pnpm store prune`
5.  Install dependencies with `pnpm i` (you might need to do this in the apps/playwright folder)
6.  Run one of the example tests by using the UI via the VSCode Playwright Extension

Expected: Due to line 6 of the file playwright.config.ts, the following log should appear in the console: `AllYourBaseAreBelongToUs`

Actual: The log `undefined` appears in the console

#### To fix this, you need to change the env path in the playwright.config.ts file to the monorepo root (fix).

7.  Change the env path in the playwright.config.ts file to the monorepo root: `dotenv.config({ path: "apps/playwright/.env" });`
8.  Run one of the example tests by using the UI via the VSCode Playwright Extension

Expected: Due to line 6 of the file playwright.config.ts, the following log should appear in the console: `AllYourBaseAreBelongToUs`

Actual: Said log appears in the console
