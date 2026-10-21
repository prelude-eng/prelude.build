# GitHub Pages and GoDaddy

The GitHub Actions workflow in `.github/workflows/deploy.yml` builds Astro with Node.js 24 and the pinned pnpm version, uploads `dist/` and deploys it to GitHub Pages on every push to `main`. It can also be started manually in the Actions tab. No deployment secret is needed: the deploy job uses GitHub's short-lived Pages OIDC credentials.

## GitHub configuration

Repository: https://github.com/prelude-eng/prelude.build

Under **Settings → Pages**, set **Source → GitHub Actions** and **Custom domain → prelude.build**. Once DNS resolves and GitHub has issued the certificate, enable **Enforce HTTPS**. The canonical domain is the apex, so `www.prelude.build` redirects there when both DNS names are configured.

Astro's `site` is already `https://prelude.build`. No repository-name `base` is needed for a custom domain. `public/CNAME` documents the intended hostname, although Actions-based Pages uses the repository's custom-domain setting rather than that file.

## GoDaddy records

Open **Domain Portfolio → prelude.build → DNS → DNS Records**. Add these five records; TTL **1 hour / 3600 seconds** is suitable.

| Type | Name | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | prelude-eng.github.io |

For IPv6, also add all four:

| Type | Name | Value |
| --- | --- | --- |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |

Replace conflicting parked/old A or AAAA records for `@`, conflicting `www` records and domain forwarding. Preserve unrelated records, especially MX and TXT records used for mail, SPF, DKIM and DMARC. Use the hostname only for the CNAME value, without `https://` or a path. Do not add a CNAME at `@`.

GitHub recommends verifying domain ownership in the organisation's **Settings → Pages**. GitHub supplies a unique TXT record; enter that exact value in GoDaddy and retain it after verification.

## Check propagation

```sh
dig +short prelude.build A
dig +short prelude.build AAAA
dig +short www.prelude.build CNAME
```

The A answers should be the four GitHub IPs above, and the CNAME should be `prelude-eng.github.io.`. DNS propagation and certificate issuance can take up to 24 hours. GitHub's Pages settings show the DNS check and certificate status.

## Headers

GitHub Pages does not apply `public/_headers`; that file is retained for hosts that support it. The production HTML carries a CSP meta tag and referrer policy. Header-only policies such as HSTS, `frame-ancestors` and Permissions-Policy require a hosting proxy if needed. The site uses only self-hosted fonts, static SVG/CSS animation and no client JavaScript.

Sources: [GitHub custom-domain configuration](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site), [GitHub Pages HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https), [Astro deployment](https://docs.astro.build/en/guides/deploy/github/).
