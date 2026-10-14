# makeafriend.net — public site

Static GitHub Pages site for **Make a Friend Ltd**, published at <https://www.makeafriend.net>.
Used as the public OAuth consent-screen surface (home page, privacy policy, terms) for Google app verification.

## Pages

| URL | File | Purpose |
| --- | --- | --- |
| `/` | `index.html` | Public home page: what the AI assistant application does, the data controls, Google data use, consulting services, contact. No login. |
| `/policy` | `policy/index.html` | Submitted Privacy Policy. Google-data categories, feature purposes, inference transfers, no general-purpose model training, security, retention and deletion. Canonical is `/policy/`. |
| `/privacy/` | `privacy/index.html` | Full copy of the same policy for previously published links; canonical points to `/policy/`. Keep both policy files identical. |
| `/tos` | `tos/index.html` | Terms of Service. |

No build step: plain HTML with inline CSS. Edit the files and push to `main`; GitHub Pages serves them.

## Consent-screen URLs (keep in sync with Google Cloud)

- Application home page: `https://www.makeafriend.net/`
- Privacy policy: `https://www.makeafriend.net/policy`
- Terms of service: `https://www.makeafriend.net/tos/`

The homepage links to the exact privacy-policy URL supplied for this verification attempt.
GitHub Pages redirects `/policy` to `/policy/`, where the full HTML policy is served.
A direct `200` is available at `/policy/` if the Console URL and all homepage links are changed
together. A normal trailing-slash redirect is not proof of the cause of Google's rejection.

## Domain notes

- `CNAME` sets the GitHub Pages custom domain to `www.makeafriend.net`.
- DNS lives at Cloudflare. The origin for this public site is `makeafriendltd.github.io`.
  GitHub Pages also supports apex A records at `185.199.108.153`, `185.199.109.153`,
  `185.199.110.153` and `185.199.111.153`.
- Cloudflare HTTP 526 means origin certificate validation failed; proxying a hostname or chaining
  CNAME records does not, by itself, prove a loop. Inspect the actual origin and certificate before
  changing DNS or weakening TLS settings. The apex redirected successfully to `www` during this audit.
- Google Search Console TXT records are verification tokens, not proof that the correct Google
  account completed verification or has access to the OAuth project.

## Before resubmitting

- Use the public `www` homepage, not an application or authentication URL that requires login.
- Keep every homepage Privacy Policy link identical to the URL submitted in Google Cloud.
- Verify that the consent-screen app name matches the application's visible name.
- Check the actual OAuth scopes against the feature and data descriptions in the policy. This
  repository does not contain the assistant backend or Cloud Console scope configuration.
- The published no-training, processor restrictions, encryption, retention and deletion language
  describes obligations the actual service must meet. Confirm provider identities, provider
  no-training settings, storage regions and deletion behavior before requesting approval.
- If the automated findings persist for these publicly readable pages, request manual review or
  reply to Google's verification email with the URLs and the changes made. A browser smoke check
  does not prove that Google's reviewer saw the same response or that branding was approved.

Guidance: [Privacy Policy](https://support.google.com/cloud/answer/13806988) and
[App Homepage](https://support.google.com/cloud/answer/13807376).
