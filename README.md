BMS Setup Guide
Google Sheets Database + Vercel Hosting
Architecture: Browser → Google Sheets API → Your Google Sheet
No backend. No server. No Render. Just a HTML file + Google.

STEP 1 — Create your Google Sheet

Go to sheets.google.com → New spreadsheet
Name it: BMS Data
Rename the first tab (bottom) to exactly: Sales
Leave it empty — the app writes the headers automatically on first use
Copy the Sheet ID from the URL:

   https://docs.google.com/spreadsheets/d/THIS_IS_YOUR_SHEET_ID/edit
Save it — you'll need it soon.

STEP 2 — Google Cloud Console setup
2a. Create a project

Go to console.cloud.google.com
Top bar → Click the project dropdown → New Project
Name: BMS App → Create

2b. Enable Google Sheets API

Left menu → APIs & Services → Library
Search: Google Sheets API
Click it → Enable

2c. Create OAuth credentials

Left menu → APIs & Services → Credentials
Click + Create Credentials → OAuth client ID
If prompted: Configure Consent Screen first (see 2d below)
Application type: Web application
Name: BMS Web App
Under Authorized JavaScript origins, add:

http://localhost:5500 (for local testing)
http://localhost:3000 (for local testing)
https://YOUR-APP.vercel.app (add after deploying to Vercel)


Leave Authorized redirect URIs empty (not needed for this flow)
Click Create
Copy your Client ID — looks like: 123456789.apps.googleusercontent.com

2d. Configure Consent Screen (if asked)

APIs & Services → OAuth consent screen
User Type: External → Create
App name: BMS
User support email: your email
Developer contact: your email
Scopes page: click Add or Remove Scopes → find Google Sheets API → check .../auth/spreadsheets → Update
Test users: Add your Gmail address
Save and Continue through all steps


⚠️ While in "Testing" mode, only test users you add can sign in.
To allow anyone: publish the app (Verification page → Publish)
For personal use, Testing mode with your email added is perfectly fine.
