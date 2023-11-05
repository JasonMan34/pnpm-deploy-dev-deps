# Repro

Run `pnpm --filter app deploy --prod out`

### Result:
```
 ERR_PNPM_WORKSPACE_PKG_NOT_FOUND  In packages/app: "@workspace/missing@workspace:*" is in the dependencies but no package named "@workspace/missing" is present in the workspace

This error happened while installing a direct dependency of /Users/jason/repos/pnpm-deploy-dev-deps/packages/app

Packages found in the workspace: pnpm-deploy-dev-deps, app
```

### Expected:
No error. `@workspace/missing` is irrelevant to the command since we're deploying in `--prod` mode and devDependencies should be ignored

### Rationale:
A Dockerfile that does not copy local-only dependencies, such as an eslint config, fails on the `deploy` stage