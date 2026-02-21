# 001 - Migrate frontend to Bun

**Date:** 2026-02-21

## Changes

- Replaced npm with Bun as the frontend package manager
- Swapped `package-lock.json` for `bun.lock`
- Updated `Dockerfile.frontend.dev` to use `oven/bun:1-alpine` base image
- Updated `Makefile` eslint target to use `bun run lint`
- Updated `scripts/deploy-frontend.py` to use `bun` for install and build
- Updated `frontend/README.md` with Bun commands (`bun install`, `bun run dev`, `bunx`)
- Added `package-lock.json` to `.gitignore` to prevent npm lockfile from returning
- Configured stack name (`factorybot-core`) and admin email in `infra-cdk/config.yaml`
- Migrated `infra-cdk` dependencies to Bun

## Why

Bun provides faster installs, faster script execution, and a simpler toolchain compared to npm.
