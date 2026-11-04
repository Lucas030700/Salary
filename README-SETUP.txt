SALARY & BUDGET PLANNER
Company-agnostic, local-only build. No login. No cloud database.

DATA STORAGE
- Planner settings: browser localStorage key salaryBudgetPlanner
- Work & Pay Records: browser localStorage key salaryMonthlyHistory
- Data stays in the browser/device where it was entered.
- No login, authentication, Supabase, cloud sync, or remote database is used.
- Use the same browser and device to access saved data.
- Clearing browser site data or using private/incognito mode may remove or prevent persistence.

PRIVACY
Planner salary, benefits, expenses, and work records are not uploaded to a cloud database. If hosted online, the hosting provider serves the app files, while planner records remain in browser storage.

FILES
- index.html: planner application
- manifest.json: installable app metadata
- sw.js: offline app cache
- icon-192.png / icon-512.png: app icons

DISPLAY
- The page uses a fixed mobile viewport and disables pinch/double-tap zoom on supported touch browsers.
- Desktop browser zoom shortcuts may still be controlled by the browser itself.
