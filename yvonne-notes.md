# Node Package Manager

### What is Package Manager?

A package _manager_ is a tool that facilitates installing/uninstalling packages. In the programming world, it's also usually important that a package manager helps install/uninstall inter-package dependencies.

A package manager, in short, is just smaller pieces of the software which were written to fulfill _even smaller and more specific aspects_ of the program.

These smaller pieces of software can sometimes be sold or offered free to use, and are often referred to as packages.

A typical application, such as a website, will depend on dozens or hundreds of packages. These packages are often small. The general idea is that you create a small building block which solves one problem and solves it well.

Examples of package manager:
Chrome extensions
Text editor package manager (for atom or sublime)
Apple APP store

### How does it help with dependencies?

A way that node modules are cataloged and installed. It helps with dependencies because it coordinates the way dependencies are structured which prevents dependencies :fire:hell:fire:.

### What is package.json, and what does npm init do?

See this cool interactive demo [here!](http://browsenpm.org/package.json)

`npm init` is the first command you will use to create a Node project. It will 'initialize' your project by adding a file called `package.json` in the root directory.

NPM will ask you some questions in your terminal after you run the command — your answers will be pre-filled into the `package.json` like this:

![](/img/package.json-example.png)

What happens when you need to edit your `package.json`? Don't worry! You can easily go into your root directory where the file lives and edit it!

### How do you use an installed package in your code?

![](/img/npm-install-example.png)

Also! Something to remember (Thanks Oli Jam!):

`--save` is for dependencies that your application needs to run (i.e. things that need to be installed on the server delivering your application).

vs. `--save-dev` is for development dependencies that your project doesn't need in production (e.g. Browsersync from above is only used whilst developing a site).
