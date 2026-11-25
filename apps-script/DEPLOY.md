# Deploy the separate BookFlow newsletter sheet

This writes to **your provided Google Sheet** only:

```text
https://docs.google.com/spreadsheets/d/1GgvO3hB2SujMlTli5iK4I-4n7aJ4-SWYRNHoalU4xfY/edit
```

The sheet ID is already set in `Code.gs`, so the Apps Script project does **not** need to be opened from the sheet. A standalone project at `script.google.com` works fine.

## Recommended: standalone Apps Script project

1. Go to:

   ```text
   https://script.google.com/home
   ```

2. Click **New project** (blue **+**).
3. Name the project, for example:

   ```text
   BookFlow Newsletter
   ```

4. Delete everything in the code editor.
5. Open `apps-script/Code.gs` in this repo, copy all of it, and paste it there.
6. Click the **Save** icon.
7. Click **Deploy** → **New deployment**.
8. Click the gear next to *Type* and choose **Web app**.
9. Set:
   - **Execute as:** Me
   - **Who has access:** Anyone
10. Click **Deploy**.
11. If Google shows **Review permissions**, continue and approve the access request.
12. Copy the **Web app URL** — it ends in `/exec`:

   ```text
   https://script.google.com/macros/s/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/exec
   ```

13. Send that `/exec` URL to me. I’ll replace the old endpoint in `script.js` and push the site.

You must be signed in with a Google account that can edit the sheet, otherwise the script will fail when it tries to write.

## Alternative: from the sheet itself

If the **Extensions → Apps Script** menu loads for you, you can use that instead:

1. Open the sheet link above.
2. **Extensions** → **Apps Script**.
3. Delete the default code, paste `apps-script/Code.gs`, save.
4. Deploy → New deployment → Web app → Execute as **Me**, access **Anyone**.
5. Approve permissions, copy the `/exec` URL, send it to me.

## Optional test

After deploying, open the `/exec` URL in a browser. It should show:

```json
{"ok":true,"message":"BookFlow newsletter endpoint is live."}
```

On the first signup, if the tab is empty, it writes the headers:

```text
Email | Valid | Reason | Page | Referrer | Time
```

It appends each signup to the `Sheet1` tab and skips duplicate emails already in that tab.

Until you send the `/exec` URL, the site still uses the old shared endpoint.
