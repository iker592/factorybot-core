# 003 - Custom Domain (agentefactory.com)

## Domain Registration
- Registered `agentefactory.com` via Route 53 ($13/yr, auto-renew, WHOIS privacy enabled)
- Route 53 hosted zone auto-created with DNS records for Amplify

## Amplify Domain Association
- Associated `agentefactory.com` and `www.agentefactory.com` with the Amplify app
- SSL certificate provisioned via Amplify Managed (ACM)
- DNS records: A alias for root domain, CNAME for www, CNAME for ACM validation

## Cognito Callback URLs
- Added `custom_domain` field to `AppConfig` interface and `config-manager.ts`
- `fast-main-stack.ts` now adds `https://{custom_domain}` to Cognito callback/logout URLs
- Google OAuth redirect will work on the custom domain after next `cdk deploy`

## Repo & Docs
- Updated GitHub repo homepage to https://agentefactory.com
- Updated mkdocs site_name to "Agente Factory" with site_url
