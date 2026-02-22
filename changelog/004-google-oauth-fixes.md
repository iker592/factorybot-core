# 004 - Google OAuth & Redirect Fixes

## ARM64 Docker Build Fix (PR #5)
- Added `docker/setup-qemu-action@v3` to CI/CD workflow for cross-platform ARM64 Docker builds
- GitHub Actions runners are x86_64; the backend Dockerfile targets `linux/arm64`
- Without QEMU emulation, the container failed with `exec format error`

## Cognito Email Attribute Fix (PR #6)
- Changed email attribute from `mutable: false` to `mutable: true` in `cognito-stack.ts`
- Federated identity providers (Google) need to write the email attribute on first login
- Required full stack teardown and redeploy since Cognito doesn't allow in-place mutability changes

## OAuth Redirect to Custom Domain (PR #7)
- Updated `deploy-frontend.py` to read `custom_domain` from `config.yaml`
- When set, `aws-exports.json` uses `https://{custom_domain}` as `redirect_uri` and `post_logout_redirect_uri`
- Previously redirected to the Amplify default URL (`main.*.amplifyapp.com`)

## Stack Recreation
- CloudFormation stack entered `UPDATE_ROLLBACK_FAILED` state due to Cognito attribute constraint
- Resolved by deleting the entire stack (`cdk destroy`) and redeploying from scratch
- Re-wired `agentefactory.com` DNS to the new Amplify app and CloudFront distribution
