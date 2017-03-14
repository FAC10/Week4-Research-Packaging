# Packaging / npm

## Dependancies

### What is a dependancy?

A dependancy is a node module required for your code to work properly. Node's power comes from its use of lots of different modules, because these modules can be (and often are) interdependant, it is important to specify those that your code is dependant on. The modules that your code is **dependant** on are referred to as **dependancies**.<br>
you define these dependancies in your package.json. You define both the name of the module and the version your code is dependant on.<br>

e.g. the "request" module is an npm module made to simplify http requests. If you use this module in your code you'll have to add it as a dependancy in your package.json. <br>
When in the root directory of your project if you run ```npm install -S <package-name>``` in your terminal you will install the package to your node_modules directory and also add it to the dependancies in your package.json. <br>
This means if someone pulls your project from github they just have to run "npm install" when in the root directory of the project and it will install all of the dependancies. (since you never push your node modules to github because you are a good developer :wink:)
<br><br>

### Why might you use a dependancy rather than writing the code from scratch?

You may have found, for example when writing a generic fetch function (to make a call to an api and return the xhr.responsetext as a json object) during the api week project, that there is a tried and tested way of writing certain bits of code. Pretty much everyone's fetch function looked the same.<br><br>
This is why we use dependancies rather than write code from scratch.<br><br>
There are certain problems in programming that have standard ways of being fixed, dependacies allow you to use tried and tested ways of solving these problems (which is why it's important to use reliable modules as dependancies) while focussing on solving the problems specific to your project.

### What have been some of the traditional problems with dependancies?

#### :hocho: Dependancy hell :hocho:
Dependancy hell refers to the problem in software where different dependacies for an app have their own sub-dependancies which conflict. To simplify [(stolen from here)](https://lexi-lambda.github.io/blog/2016/08/24/understanding-the-npm-dependency-model/):
![](img/dependancy-tree.png)
<br>
In short a traditional dependancy model will only allow one version of each dependancy, meaning if different modules depend on the same module but different versions, you'll have problems. <br>
Becuase in the node/npm dependancy model each individual module has its own node-modules file and package.json to define its dependancies you never get conflicts from different modules depending on different versions of the same module.


## Node Package Manager

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

## NPM install

### Installing a package globally

 npm install -g MODULE_NAME: install MODULE_NAME globally. This drops modules in {prefix}/lib/node_modules, so that they are accessible globally (not only in your current working directory).

 Tools that your projects do not depend on can be installed globally.

### Installing a package as a dependency

npm install --save MODULE_NAME: installs MODULE_NAME locally (in the current working directory) and adds it as a dependency in the package.json. i.e. a dependency that is required for your application to run

```
"dependencies": {
  "nodemon": "^1.11.0"
}
```

### Installing a package as a development dependency

npm install --save-dev MODULE_NAME: installs MODULE_NAME locally and adds it as a development dependency in the package.json. i.e. a dependency that is only needed for development and not for production.

```
"devDependencies": {
  "browser-sync": "^2.18.8"
  }
```

E.g. browser sync. This is a nice module for development, as the browser auto-refreshes when any saved changes are detected in your files

Dependencies are useful, because they ensure that other people working on your project know which modules are required for production and which are only required for development.

When you clone a repo, `npm install` will install both dependencies and devDependencies listed in package.json. Use `npm install --only=production` to install only dependencies, and `npm install --only=dev` to install only devDependencies

### Why is it normally a bad idea to install a package globally?

If your project depends on a package, __it should be listed in your package.json file as a dependency__ and installed locally in your project, rather than globally.

This way, if someone is working on your project, all they have to do is `npm install` to ensure that all dependencies are installed. It also ensures that the correct version of the module for your project is installed.

### Resources
https://nodejs.org/en/blog/npm/npm-1-0-global-vs-local-installation/
http://stackoverflow.com/questions/9268259/how-do-you-prevent-install-of-devdependencies-npm-modules-for-node-js-package
https://www.smashingmagazine.com/2016/01/issue-with-global-node-npm-packages/

## Package files

**In general, the rule of thumb is:**
- If you’re installing something that you want to use in your program, using ```require('whatever')```, then install it locally, at the root of your project.
- If you’re installing something that you want to use in your shell, on the command line or something, install it globally, so that its binaries end up in your PATH environment variable.

**Reasons to cut down on our use of global module installation:**
- First of all, global modules are not listed as dependencies in your projects, even though your project depends on them, which causes extra steps for others using your application.
- You can run into conflicts due to having the wrong version of the module installed.

**Where does NPM install packages?**
```npm list --global``` or ```npm list --global --depth=0``` - list the global packages we have installed and the corresponding directory

**What about non-global packages?**
Use ```npm list``` instead.

 **How do you prevent Git from including these files in your repository?**  
A gitignore file specifies intentionally untracked files that Git should ignore. Files already tracked by Git are not affected.
  [More info here](https://git-scm.com/docs/gitignore)


**Why is it important to make sure that installed packages aren't included in your repositories?**

  Without matching .gitignore rules, these files will appear in the "untracked files" section of git status output. If this list is long, then new files you actually do want to add to the git repository may be hidden in the noise, leading to mistakes whereby you fail to commit all the files required to make your program compile. By using .gitignore rules in a .gitignore file, the extraneous files you never want to commit will be removed from the git status output, making it more likely that you will see the new file that you actually wanted to add to the repository in the list of untracked files.
