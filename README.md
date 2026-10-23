# makeafriend.net — public site

Static GitHub Pages site for **Makeafriend AI Assistant**, developed by Make a Friend Ltd and
published at <https://www.makeafriend.net>. The site supplies the public homepage, privacy policy
and terms for Google OAuth branding verification.

## Pages

| URL | File | Purpose |
| --- | --- | --- |
| `/` | `index.html` | Public home page: local-first AI assistance, user-selected models, optional connections, consulting and contact. No login. |
| `/privacy` | `privacy/index.html` | Privacy Policy URL in the latest verification finding. Local files, model-endpoint transfers, Google Limited Use, retention and deletion. Canonical is `/privacy/`. |
| `/policy/` | `policy/index.html` | Full policy copy for older published links; canonical points to `/privacy/`. Keep both policy files identical. |
| `/tos` | `tos/index.html` | Terms of Service. |

No build step: plain HTML with inline CSS. Edit the files and push to `main`; GitHub Pages serves them.

## Confirmed product facts

The owner clarified these facts on 15 October 2026:

- The exact application name is **Makeafriend AI Assistant**.
- It is model-agnostic, not tied to a particular hosted AI provider.
- Assistant application data is saved as local files in the user's environment; Make a Friend Ltd
  does not operate an online assistant-data store.

Do not reintroduce invented hosted storage regions, central account-deletion workflows,
automatic at-rest encryption guarantees or fixed 30-day/12-month assistant-data retention.
Local storage does not mean no network processing: an optional Google connection communicates
with Google, and a user-selected hosted model receives its task inputs. Its own retention settings
must not be represented as a guarantee made by Makeafriend. Google-data processing still requires
Limited Use and no-generalized-training protections, regardless of model choice.

## Consent-screen URLs (keep in sync with Google Cloud)

- Application home page: `https://www.makeafriend.net/`
- Privacy policy: `https://www.makeafriend.net/privacy`
- Terms of service: `https://www.makeafriend.net/tos/`

The latest reported verification URL is `/privacy`; earlier attempts named `/policy`.
Homepage and Terms links now use the exact `/privacy` URL, and both policy copies declare
`/privacy/` as canonical. GitHub Pages redirects `/privacy` to `/privacy/` to serve the HTML.
Do not treat that ordinary directory redirect as proof of the cause of Google's rejection.
Keep the saved Branding fields, homepage links and canonical route consistent rather than
switching between paths in successive attempts.

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

## Publishing status is not verification approval

Audience → **Publish app** changes a client's publishing status from Testing to In production.
Branding review and any required sensitive/restricted-scope review are separate processes.
The status label "In production" is not the same as Google's policy definition of a production
app, which excludes genuine personal use. Do not mark a publicly distributed assistant as
personal use just because its data is stored locally.

[Rclone's current instructions](https://rclone.org/drive/#making-your-own-client-id) explicitly
describe homepage and privacy-policy fields blocking publishing even for a personal client.
[Google documents a personal-use verification exception](https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification#personal-use).
That exception is not evidence that the Console will accept missing Branding fields.
The [August report](https://forum.rclone.org/t/cant-configure-google-drive-client-id/54191)
and [October report](https://discuss.google.dev/t/personal-use-desktop-oauth-publish-app-disabled-with-no-branding-field-error/407592)
describe the UI behavior; they are not an official rollout announcement or a guarantee that a
particular client can publish without review.

For this application, keep the existing project/client and use:

| Branding field | Value |
| --- | --- |
| App name | `Makeafriend AI Assistant` |
| Application home page | `https://www.makeafriend.net/` |
| Privacy policy | `https://www.makeafriend.net/privacy` |
| Terms of service | `https://www.makeafriend.net/tos/` |
| Authorized domain | `makeafriend.net` (no scheme, path or `www`) |
| User support / developer email | A reachable address controlled by the project owner; confirm routing before using a domain alias. |

Save Branding, then check Audience → Publish app. If the button is still disabled, inspect the
actual saved fields and project ID rather than changing the public site's purpose or copying a
sample policy. Domain verification must be completed by an account associated with the project.
This site already uses an owned domain; a new free site or a different paid domain is unnecessary.

After the Console confirms In production, obtain a fresh authorization using the existing gog
configuration and its `--force-consent` option. A status change does not reissue tokens obtained
while the client was in Testing. Use the scopes required by your actual gog operation, not a
broader scope list copied from rclone's Drive example.
Publishing and authorization cannot be completed by a website deployment; keep client secrets
and tokens outside this public repository.

Google's [OAuth policy](https://developers.google.com/identity/protocols/oauth2/policies#handle-user-tokens-securely)
requires encrypted token storage at rest even for local deployments. Verify the actual token
backend before authorizing; this static site does not implement or certify token encryption.

## Public contact links

Email links are wrapped in Cloudflare's documented `<!--email_off-->…<!--/email_off-->` markers.
This preserves native `mailto:` links without JavaScript; encoding only `@` as an HTML entity
did not stop Cloudflare rewriting the link. Keep the exclusions when editing contact or
deletion-request addresses. This improves accessibility, not proof of Google's approval.
See [Cloudflare Email Address Obfuscation](https://developers.cloudflare.com/waf/tools/scrape-shield/email-address-obfuscation/).

## Before resubmitting

- Use the public `www` homepage, not an application or authentication URL that requires login.
- Keep every homepage Privacy Policy link identical to the URL submitted in Google Cloud.
- Verify that the consent-screen app name matches the application's visible name.
- Check the actual OAuth scopes against the feature and data descriptions in the policy. This
  repository does not contain the assistant backend or Cloud Console scope configuration.
- Verify the actual OAuth scopes and behavior of the configured model endpoint. The policy does
  not promise that arbitrary hosted endpoints retain nothing or automatically satisfy Google's rules.
- Confirm the documented local data locations and deletion procedure against the actual assistant.
  Do not claim the developer can remotely inspect or delete user-controlled local files.
- If the automated findings persist for these publicly readable pages, request manual review or
  reply to Google's verification email with the URLs and the changes made. A browser smoke check
  does not prove that Google's reviewer saw the same response or that branding was approved.

For a recurring finding after deployment, obtain the actual Google Cloud project ID, the saved
and draft Branding fields, requested OAuth scopes, and the verification attempt timestamp.
In Cloudflare request/security events for that time, inspect the hostname, URI, action, status,
user agent and Ray ID to distinguish the intended public pages from an authentication endpoint
or an actual challenge. Do not assume that spoofing a Googlebot user agent reproduces Google's
reviewer, and do not disable zone-wide security based only on the rejection banner.

Guidance: [Privacy Policy](https://support.google.com/cloud/answer/13806988) and
[App Homepage](https://support.google.com/cloud/answer/13807376).
