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
