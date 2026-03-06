# writecodefor.me

Teaser homepage for [writecodefor.me](https://writecodefor.me) — something extraordinary is being crafted.

---

## Enabling SSL / HTTPS for this site

This site is hosted on **GitHub Pages** with the custom domain `writecodefor.me` (configured via the `CNAME` file). GitHub Pages automatically provisions a **free SSL/TLS certificate** through [Let's Encrypt](https://letsencrypt.org/) — no certificate file needs to be added to this repository.

### Prerequisites

Before GitHub can issue and activate the certificate, two things must be true:

#### 1. DNS records must point to GitHub Pages

In your domain registrar's DNS panel, add the following **A records** for the apex domain (`writecodefor.me`):

| Type | Name | Value |
|------|------|-------|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

And a **CNAME record** for the `www` subdomain:

| Type | Name | Value |
|------|------|-------|
| CNAME | `www` | `oppenheimer229.github.io` |

> **Note:** The CNAME value above must match the GitHub Pages URL for this repository (`<your-github-username>.github.io`).

> DNS changes can take up to 48 hours to propagate worldwide. You can verify propagation at [dnschecker.org](https://dnschecker.org).

#### 2. Enforce HTTPS must be enabled in GitHub repository settings

1. Go to this repository on GitHub.
2. Click **Settings** → **Pages** (in the left sidebar).
3. Under **Custom domain**, confirm `writecodefor.me` is saved.
4. Wait for the **"DNS check successful"** message to appear.
5. Once that appears, tick the **"Enforce HTTPS"** checkbox.

GitHub will automatically provision the Let's Encrypt certificate and serve all traffic over `https://` once both steps above are complete. No certificate files or private keys are ever stored in this repository — GitHub manages the full certificate lifecycle (issuance, renewal every 90 days) on your behalf.

### Troubleshooting

| Symptom | Likely cause | Fix |
|---------|-------------|-----|
| "Enforce HTTPS" checkbox is greyed out | DNS hasn't propagated yet, or records are wrong | Verify DNS records are correct and wait; check Settings → Pages for the specific error message |
| Certificate error in browser | Old DNS cached on your machine | Flush DNS cache or try a different network/browser |
| "Domain's DNS record could not be retrieved" | Missing or wrong A/CNAME records | Double-check the DNS values in the table above |
