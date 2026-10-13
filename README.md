# makeafriend.net — public site

Static GitHub Pages site for **Make a Friend Ltd**, published at <https://www.makeafriend.net>.
Used as the public OAuth consent-screen surface (home page, privacy policy, terms) for Google app verification.

## Pages

| URL | File | Purpose |
| --- | --- | --- |
| `/` | `index.html` | Public home page: what the company does, what the AI assistant application does with Google data, contact. No login. |
| `/privacy` | `privacy/index.html` | Privacy Policy (canonical). Data collected, purposes, Google API Limited Use commitments, retention, rights. |
| `/policy` | `policy/index.html` | Same Privacy Policy content, kept so an older consent-screen link still resolves. Canonical points to `/privacy`. |
| `/tos` | `tos/index.html` | Terms of Service. |

No build step: plain HTML with inline CSS. Edit the files and push to `main`; GitHub Pages serves them.

## Consent-screen URLs (keep in sync with Google Cloud)

- Application home page: `https://www.makeafriend.net`
- Privacy policy: `https://www.makeafriend.net/privacy`
- Terms of service: `https://www.makeafriend.net/tos`

## Domain notes

- `CNAME` sets the GitHub Pages custom domain to `www.makeafriend.net`.
- DNS for `makeafriend.net` lives at Cloudflare. The apex must resolve to GitHub Pages
  (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, DNS-only) so GitHub can
  issue the apex certificate and redirect it to `www`. Proxying the apex through Cloudflare blocks
  certificate issuance and returns HTTP 526.
- Domain ownership for Google verification is done in Google Search Console (domain property via DNS TXT).
