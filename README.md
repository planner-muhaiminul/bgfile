# Bashundhara Project Control Desk

A responsive, Swiss-inspired dashboard for tracking project-wise regulatory approvals and renewals across RAJUK, DTCA, DoE, Fire Service and other departments.

## Included
- Responsive desktop and mobile dashboard
- Current approval register with project/department/status/deadline filters
- Deadline radar (overdue and next 30 days)
- Add/edit/remove records
- Append-only status/remarks history in Google Sheets
- CSV export of the currently filtered register
- Google Apps Script backend (`Code.gs`)
- Demo records to preview the design

## Files
- `index.html` — front-end dashboard
- `Code.gs` — Google Apps Script backend
- `README.md` — setup and publishing steps

## Publish with Google Sheets + GitHub Pages

### 1. Create the Google Sheet
1. Create a new Google Spreadsheet.
2. Open **Extensions → Apps Script**.
3. Replace the editor content with `Code.gs` from this folder.
4. Replace `SET_A_LONG_RANDOM_KEY` with a long random API key.
5. Save, select `setupSheets` and click **Run** once; approve the permissions.
6. Return to the spreadsheet and confirm that `Projects` and `History` tabs exist.

### 2. Deploy Apps Script
1. Click **Deploy → New deployment → Web app**.
2. Execute as: **Me**.
3. Access: **Anyone with the link** only if permitted by your organisation's security policy.
4. Deploy and copy the URL ending in `/exec`.

**Security:** This starter implementation uses a shared key. If you publish the front end publicly on GitHub Pages, the key can be discovered in browser storage/network traffic. Do not use this setup for confidential records without adding Google Workspace authentication or a secure proxy/backend. Follow your organisation's IT policy.

### 3. Publish the front end
1. Create a GitHub repository, e.g. `bashundhara-project-control`.
2. Upload `index.html` and this `README.md`.
3. In the repository, open **Settings → Pages**.
4. Select **Deploy from a branch**, choose `main` and `/ (root)`, then Save.
5. Open the published GitHub Pages URL.

### 4. Connect the dashboard
1. Open the dashboard and select **Connect Sheet**.
2. Paste the Apps Script `/exec` URL and the same API key.
3. Click **Test connection**, then **Save & sync**.

## Important notes
- Demo mode is local to the browser and is not shared between users.
- Google Sheets mode shares the current records and history.
- A deleted record is removed from the current register but a removal event is written to History. If you require full archival of every deleted record, adjust the backend to mark records as archived rather than deleting the row.
- This is a working starter template, not a certified regulatory compliance system. Verify the official validity period and renewal requirements for each permit with the relevant authority.
- Use consistent dates (`YYYY-MM-DD`) and record the authority reference/memo number, owner, last checked date and next action.
