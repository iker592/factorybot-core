# 002 - Google OAuth Login & CI/CD Pipeline

## Google OAuth via Cognito
- Added Google as a federated identity provider in Cognito User Pool
- Users can now sign in with their Google account alongside email/password
- Client secret loaded from `GOOGLE_OAUTH_CLIENT_SECRET` env var (not stored in code)
- Updated `config-manager.ts` with `google_oauth` config interface
- Updated `cognito-stack.ts` with Google provider, attribute mapping, and supported identity providers

## GitHub Pages Documentation
- Added `.github/workflows/deploy-docs.yml` to auto-deploy MkDocs on pushes to `.mkdocs/`
- Updated `.mkdocs/mkdocs.yml` with factorybot-core repo name and URL
- Docs live at https://iker592.github.io/factorybot-core/

## CI/CD Pipeline
- Added `.github/workflows/deploy.yml` for automatic AWS deployment on pushes to `main`
- Two-stage pipeline: backend (CDK) then frontend (Amplify)
- Uses GitHub OIDC to assume IAM role `factorybot-core-github-actions` — no static access keys
- Skips deployment for docs-only or changelog-only changes
- GitHub secrets configured: `AWS_ROLE_ARN`, `GOOGLE_OAUTH_CLIENT_SECRET`
