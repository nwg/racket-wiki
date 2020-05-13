## [[Contribute to Racket]] 
* [Building, Distributing, and Contributing to Racket](https://docs.racket-lang.org/racket-build-guide/index.html)
* [Tutorial: Contributing to Racket](https://blog.racket-lang.org/2017/09/tutorial-contributing-to-racket.html) describes how to contribute to racket documentation(e.g. fix a typo), the language itself or a package in the main distribution. (by Ben Greenman)

**Summary**

1. `raco pkg update --clone <PKG>`
2. fork the racket/<PKG> repo on GitHub
3. add your fork as a remote: `git remote add fork https://github.com/<YOUR-USERNAME>/<PKG>`
4. make a new branch, `git checkout -b my-edits`
5. do edits
6. rebuild documentation using `scribble colour.scrbl` or `raco pkg update gui`  
7. commit changes, `git commit`
8. push to the fork, `git push fork my-edits`
9. create a pull request on GitHub

If you are new to GitHub, the following GitHub documentation is helpful;

* [About pull requests](https://help.github.com/en/articles/about-pull-requests)
* [Creating a pull request](https://help.github.com/en/articles/creating-a-pull-request)