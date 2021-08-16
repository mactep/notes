# GitHub Packages NPM registry

#TODO:
- Check if it's needed to manually generate a GitHub token.

## GitHub Actions
Bellow is a valid workflow to build a Angular library in the branch
"production" and publish it as a NPM package. `build:prod` is a custom script
to run `ng build` with the `--prod` flag, needed in order to publish Angular
packages.
```
name: Build Angular library

on:
  push:
    branches: production

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
        with:
          ref: production

      - uses: actions/setup-node@v1
        with:
          node-version: 14
          registry-url: 'https://npm.pkg.github.com/'
          # Defaults to the user or organization that owns the workflow file
          scope: '@OWNER'

      - name: build and deploy
        run: |
          npm install
          npm run build:prod components
          cd dist/components
          npm publish
        env:
          NODE_AUTH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Installing from a package registry
- Create a `.npmrc` in your project with the following contents:
```
//npm.pkg.github.com/:_authToken=TOKEN
registry=https://npm.pkg.github.com/OWNER
```
Where `TOKEN` is the auth token generated inside GitHub and OWNER is the owner
of the repository.

## Caveats
- If the package name isn't the same as the repository name, repository url
  should be specified inside the corresponding `package.json` as follows:
  ```
  "name": "@OWNER/package-name-that-differs",
  "repository": {
    "type": "git",
    "url": "https://github.com/OWNER/repo-name"
  },
  ```
- Apparently, package names should be scoped. i.e. `@OWNER/package-name`.
- You have to bump the package version to publish a new one.
- Caveats from [Creating Angular Libraries](202101291530_angular_component_library.md)
  may apply too.


[Getting Started GitHub Packages](https://docs.github.com/en/packages/quickstart)
[Configuring npm for use with GitHub Packages](https://docs.github.com/en/packages/guides/configuring-npm-for-use-with-github-packages#installing-a-package)

#ci/cd
#github
#npm
