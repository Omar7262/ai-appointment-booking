# Deploy the separate BookFlow newsletter sheet

This creates a **new Google Sheet** named **BookFlow Newsletter Signups**. It will not write to the old interior-design sheet anymore.

## Steps

1. Open https://script.google.com/
2. Create a new project.
3. Replace everything in `Code.gs` with the contents of `apps-script/Code.gs` in this repo.
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

The first real signup creates the sheet automatically and writes the headers:

```text
Email | Valid | Reason | Page | Referrer | Time
```

Until step 9 is done, the site still uses the old shared endpoint.
