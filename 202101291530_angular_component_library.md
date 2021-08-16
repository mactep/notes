# Creating Angular libraries

## Creating components
```
ng new my-library
cd my-library
ng generate library my-library
```
Creates a new Angular workspace with an application, witch will be used to test
our library, and a library were we're going to create the components. The
library and the workspace have the same name to let us publish the package to
GitHub later on.

## Building the library
```
ng build my-library --prod
```
It builds the library and add it to `paths` in `tsconfig.json`, meaning that
you can import it simply calling `import {} from 'my-library'`.

## Development workflow
To test our library without compiling it every time, we're going to import it
directly into the application, rebuilding it automatically inside `ng serve`.
To do that simply import the library as `import { MyLibraryModyle } from
'projects/my-library/src/public-api';`. Then just develop as if it was a
component inside your application. Note that this may hide some errors due to
the different environment it's running.

## Publishing the library
```
ng build my-lib --prod
cd dist/my-lib
npm publish
```

Refer to [GitHub Packages](./202101291616_github_packages.md) to see how to
publish it to a private registry on GitHub.

## Necessary steps (maybe)
- Put library dependencies inside peerDependencies of it's own package.json
  file.
- To build the library it's easier to put all the peerDependencies inside the
  devDependencies of the root project. This way you can run `npm i` and `npm
  run build my-lib` at the root. It's a caveat since Angular insists that you
  put library dependencies as peers. That means they're not installed via `npm
  i`.

[Creating libraries](https://angular.io/guide/creating-libraries)
[How to publish on GitHub Packages](https://blexin.com/en/blog-en/creating-angular-components-libraries/)

#javascript
#nodejs
#angular
#webdev
#github
#ci/cd
