###Installing a package globally

 npm install -g MODULE_NAME: install MODULE_NAME globally. This drops modules in {prefix}/lib/node_modules, so that they are accessible globally (not only in your current working directory).

 Tools that your projects do not depend on can be installed globally.

###Installing a package as a dependency

npm install --save MODULE_NAME: installs MODULE_NAME locally (in the current working directory) and adds it as a dependency in the package.json. i.e. a dependency that is required for your application to run

```
"dependencies": {
  "nodemon": "^1.11.0"
}
```

###Installing a package as a development dependency

npm install --save-dev MODULE_NAME: installs MODULE_NAME locally and adds it as a development dependency in the package.json. i.e. a dependency that is only needed for development and not for production.

```
"devDependencies": {
  "browser-sync": "^2.18.8"
  }
```

E.g. browser sync. This is a nice module for development, as the browser auto-refreshes when any saved changes are detected in your files

Dependencies are useful, because they ensure that other people working on your project know which modules are required for production and which are only required for development.

When you clone a repo, `npm install` will install both dependencies and devDependencies listed in package.json. Use `npm install --only=production` to install only dependencies, and `npm install --only=dev` to install only devDependencies

###Why is it normally a bad idea to install a package globally?

If your project depends on a package, __it should be listed in your package.json file as a dependency__ and installed locally in your project, rather than globally.

This way, if someone is working on your project, all they have to do is `npm install` to ensure that all dependencies are installed. It also ensures that the correct version of the module for your project is installed.

###Resources
https://nodejs.org/en/blog/npm/npm-1-0-global-vs-local-installation/
http://stackoverflow.com/questions/9268259/how-do-you-prevent-install-of-devdependencies-npm-modules-for-node-js-package
https://www.smashingmagazine.com/2016/01/issue-with-global-node-npm-packages/
