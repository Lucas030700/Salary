EMERSON SALARY PLANNER CLOUD v19

1. In Supabase, open SQL Editor > New query.
2. Open supabase-setup.sql, copy all SQL, paste into the editor, and Run.
3. In Supabase Authentication > URL Configuration, set Site URL to your Cloudflare Worker URL.
   Add the same URL to Redirect URLs if email confirmation is enabled.
4. Deploy the contents of this folder to the existing Cloudflare Worker.
5. Open the Worker URL. Create an account with email/password.
6. On the first sign-in, the app migrates the current device's saved planner settings and monthly history to Supabase.
7. Sign in with the same account on PC and iPhone to access shared data.

IMPORTANT:
- Browser code contains only the Supabase publishable key. Never put a secret/service_role key in index.html.
- Do not enable public table access. The supplied SQL enables RLS and restricts each row to its owner.
- If email confirmation is enabled, confirm the email before signing in.
- This is a first connected build. Test with a small test account and verify records before relying on it as the only copy.

AUTO-SAVE / SYNC UPDATE:
- Planner inputs now auto-save the complete salary/benefits state after changes.
- Monthly history is saved whenever a record or bill assignment is changed.
- The cloud bridge uploads changes to planner_data; Realtime receives INSERT/UPDATE events.
- The manual Save button is hidden; no manual save is required.

VERSION 21 SYNC FIX:
- Planner auto-save explicitly queues cloud sync after calculating and persisting settings.
- Monthly history save explicitly queues cloud sync.
- Storage interception no longer relies on strict localStorage object identity.
- Uploads are serialized; changes made during an upload queue a follow-up upload.
- Realtime listener remains enabled for INSERT/UPDATE events.
Deploy this version's extracted files over the existing Cloudflare Worker. No new Supabase project or SQL migration is required.

V22 SYNC CHANGE:
- Adds a one-second live planner state watcher after login.
- Detects changes in the actual planner controls and queues cloud upload.
- Bumps service-worker cache version to v22.

V23 DIRECT CONTROL SYNC:
- Cloud upload now snapshots the live planner controls via state() rather than relying only on storage.
- Captures input/change events on planner controls and queues the upload.
- The monthly history storage hook remains enabled.
- Cache version bumped to v23.

V24 CLOUD SYNC FIX:
- Cloud payload now reads the live planner state() function.
- Direct input/change listeners capture slider, select, checkbox and text edits.
- Changes are queued for Supabase upload after a short debounce.
- Service worker cache version bumped to v24.


Version 25 update: service worker cache version bumped and app shell uses network-first loading. Supabase SQL/schema/policies are unchanged.

Version 25.1: keeps v25 authentication; initial cloud hydration and Realtime changes apply in-place without page reload; remote changes do not trigger local autosave. SQL unchanged.
