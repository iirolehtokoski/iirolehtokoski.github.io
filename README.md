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
