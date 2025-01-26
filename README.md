# Next.js 15 App Router Route Conflict

This repository demonstrates a subtle issue in Next.js 15's App Router when both the `pages` directory and the `app` directory contain routes with the same path.  The App Router unexpectedly prioritizes the route in the `app` directory, even if the `pages` directory route is perfectly valid.

## Problem

When you have both `pages/index.js` and `app/page.js`, Next.js 15 will only render the content from `app/page.js`. This behavior might not be immediately obvious and can lead to unexpected results, especially during migrations from older Next.js versions.

## Solution

The simplest way to resolve this conflict is to remove either the `pages/index.js` or `app/page.js` file, depending on the desired behavior. If you wish to keep functionality from both files you will need to refactor your code to consolidate the routes into one directory (preferably `app` for newer projects) and use components or layout components for code reuse. In some scenarios you may need to make use of the `not-found` page. 

## How to reproduce

1. Clone this repository.
2. Run `npm install`.
3. Run `npm run dev`.
4. Navigate to `/` in your browser. You should see 'Hello from app directory'.
5. Comment out `app/page.js`. Refresh. Now you will see 'Hello'.