# iirolehtokoski.fi

Static one-page site (no build step, no trackers). Hosted on GitHub Pages.

## To fill in
- **LinkedIn:** the button points to a guessed URL `https://www.linkedin.com/in/iirolehtokoski/` – check it, fix if needed, then optionally add it to JSON-LD `sameAs`.
- **Photo:** save a square photo as `assets/profile.jpg` and replace the `<div class="avatar">IL</div>` with the `<img>` shown in the HTML comment.

## Deploy
```
git remote add origin git@github.com:iirolehtokoski/iirolehtokoski.github.io.git
git push -u origin main
```
GitHub → repo Settings → Pages: Source "Deploy from a branch", branch `main`, folder `/ (root)`.

## OVH DNS (Web Cloud → Domain names → iirolehtokoski.fi → DNS zone)
Remove existing A/AAAA records for the apex (and any OVH parking/redirect), then add:

| Type | Subdomain | Target |
|---|---|---|
| A | (empty) | 185.199.108.153 |
| A | (empty) | 185.199.109.153 |
| A | (empty) | 185.199.110.153 |
| A | (empty) | 185.199.111.153 |
| AAAA (optional) | (empty) | 2606:50c0:8000::153 |
| AAAA (optional) | (empty) | 2606:50c0:8001::153 |
| AAAA (optional) | (empty) | 2606:50c0:8002::153 |
| AAAA (optional) | (empty) | 2606:50c0:8003::153 |
| CNAME | www | iirolehtokoski.github.io. |

Then in GitHub Pages settings set Custom domain to `iirolehtokoski.fi` (the `CNAME` file already contains it), wait for the DNS check, and tick **Enforce HTTPS** (certificate can take up to ~1 h). Optionally verify the domain under GitHub profile Settings → Pages.

## Contact form

Messages go through [FormSubmit](https://formsubmit.co/) (free, no account, no server). The recipient is one line in `index.html`: the form `action`.

After deploy, once:

1. Open the site, choose **Contact**, and send one message. Type the characters shown, then complete the CAPTCHA on the next page.
2. FormSubmit emails **iiro.lehtokoski@gmail.com** a confirmation. Open it and activate the form. Until then, submissions are held, not delivered. After activation they arrive, including any that were waiting.
3. That confirmation includes a random alias. Replace `iiro.lehtokoski@gmail.com` in the form `action` with it (`https://formsubmit.co/your-random-string`) so the address is not in the page.

reCAPTCHA stays on (`_captcha` is `true`). A hidden `_honey` field drops submissions that fill every input. The thank-you page is `thanks.html`.
