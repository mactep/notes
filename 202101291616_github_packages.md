# GitHub Packages NPM registry

#TODO:
- Check if there's some additional configuration such as setting up GitHub token
and setting up `package.json` file.
- Check whether or not it's needed to set "scope" variable and/or the
  "@USERNAME/REPOSITORY-NAME" in package.json.

Bellow is a valid workflow to build a Angular library in the branch
"production" and publish it as a NPM package. Notice that the package name
should be the same as the repository name. `build:prod` is a custom script to
run `ng build` with the `--prod` flag, needed in order to publish packages.
```
name: Build Angular components

on:
  push:
    branches: production

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - uses: actions/setup-node@v1
        with:
          node-version: 14
          registry-url: 'https://npm.pkg.github.com/'
          scope: '@mactep'

      - name: build and deploy
        run: |
          npm install
          npm run build:prod components
          cd dist/components
          npm publish
        env:
          NODE_AUTH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

[Getting Started GitHub
Packages](https://docs.github.com/en/packages/quickstart)

#github
#npm
#ci/cd
