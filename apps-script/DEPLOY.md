# Deploy the separate BookFlow newsletter sheet

This writes to **your provided Google Sheet** only:

```text
https://docs.google.com/spreadsheets/d/1GgvO3hB2SujMlTli5iK4I-4n7aJ4-SWYRNHoalU4xfY/edit
```

The sheet ID is already set in `Code.gs`. It will **not** write to the old interior-design sheet anymore.

## Steps

1. Open your sheet:
   https://docs.google.com/spreadsheets/d/1GgvO3hB2SujMlTli5iK4I-4n7aJ4-SWYRNHoalU4xfY/edit
2. Go to **Extensions** → **Apps Script**.
3. Delete everything in the editor and paste the full contents of `apps-script/Code.gs` from this repo.
4. Click **Deploy** → **New deployment**.
5. Click the gear next to *Type* and choose **Web app**.
6. Set:
   - **Execute as:** Me
   - **Who has access:** Anyone
7. Click **Deploy**, then approve the Google permission screen.
8. Copy the **Web app URL** — it ends in `/exec`. It looks like:

   ```text
   https://script.google.com/macros/s/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/exec
   ```

9. Send that URL to me. I will replace this line in `script.js`:

   ```js
   sheetEndpoint: "OLD_URL",
   ```

   with your new `/exec` URL, then push the site.

## Optional test

After deploying, open the `/exec` URL in a browser. It should show:

```json
{"ok":true,"message":"BookFlow newsletter endpoint is live."}
```

On the first signup, if the tab is empty, it writes the headers:

```text
Email | Valid | Reason | Page | Referrer | Time
```

It appends each new signup to the same tab (`Sheet1` by default) and skips duplicate emails already in that tab.

Until step 9 is done, the site still uses the old shared endpoint.
