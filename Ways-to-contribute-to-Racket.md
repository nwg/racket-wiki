

### New: [Tutorial: Contributing to Racket](https://blog.racket-lang.org/2017/09/tutorial-contributing-to-racket.html) by Ben Greenman

see also
* [issues tagged 'good-first-issue'](https://github.com/racket/racket/issues?utf8=✓&q=is%3Aissue+is%3Aopen++label%3Agood-first-issue+) in <https://github.com/racket/racket>
* [issues tagged 'good-first-bug'](https://github.com/racket/typed-racket/issues?q=is%3Aopen+is%3Aissue+label%3Agood-first-bug) in <https://github.com/racket/typed-racket>


## Beginners start here:
### An important way you can contribute even if you are very new to Racket;
> While Racket is much better documented than most free software, it
could be improved.  Debugging documentation requires a supply of
ignorance, which is rapidly used up as documentation testers
learn what the documentation means.  **So when you find the**
**documentation obscure**, **_treat it as a documentation bug and report it_**.
Maybe, when you become an expert and your supply of ignorance has run
out, you can even propose patches to improve that documentation!  

### ...and how to **report it** ? 
* Send an email with your observations and suggestions to the [Racket mailing list](https://lists.racket-lang.org) (Racket has a friendly community that welcomes feedback)

***

the following is from <https://github.com/racket/racket/blob/a8e3f57ebd3e0a827222a060c87c88fa28fefc1c/CONTRIBUTING.md> via <https://github.com/racket/racket/pull/2523>

***
`CONTRIBUTING.md`

# Forking the Repository

If you want to contribute to Racket, it's a good idea to fork the repository so	you have your own version.  The process is simple:

* Log in to GitHub (create an account if necessary)
* Go to https://github.com/racket/racket
* Click 'Fork' at the top right, just underneath the black bar at top of page
 
You now have your own version of the repository.  As a general policy, all changes should be made to your fork.

# Making changes
### Summary
The basic procedure is to find the error in the main repository, change to your own repository, make the change, then submit a pull request so that the Racket maintainers can review and integrate your change.  The process is relatively straightforward:
* Log in to GitHub
* Go to the main Racket repository:  https://github.com/racket/racket
* Search for the text of the error so you know what file the error is in (the search box is at top left)
* Go to that file in your own fork (easy way:  edit the URL by replacing https://github.com/racket/racket/ with https://github.com/[MY-USERNAME]/racket/)
* Edit the file
* Commit and send a pull request

## Details
Be sure that you're searching in the main Racket repository (link above) instead of in your own fork.  Github does not allow searching in forks unless the fork has more stars than the parent repo.
* Log in to GitHub
* Go to https://github.com/racket/racket
* Click in the search field at the top left of the page.  (It's grey on a grey background so can be hard to notice)
* Paste the text of the thing you're trying to find
* Find the relevant page in the search results, click the link to go to it
* Go to that file in your own fork (easy way:  edit the URL by replacing https://github.com/racket/racket/ with https://github.com/[MY-USERNAME]/racket/)
* Look for the 'Branch' droplist.  It's on the left side at the same level as the green 'Clone or Download' button (which is on the right).  This will tell you what branch you're on. It might be something unhelpful like 'Tree: 5bb83...'
* Click on the dropdown, choose an existing branch or create a new one
* Click the edit button (pen icon) on the right hand side, just above the contents of the file
* Make your changes
* Scroll to the bottom of the page, enter a message that describes what you did
* Choose the radio button that says "*Create a new branch for this commit and start a pull request. Learn more about pull requests*"  It will propose a branch name for you.
* Click the green "*Propose File Change*"
* Click on the 'Pull Requests' button, just below the name of the repository
* Find the branch name that you just created, click 'Compare and pull request'
* Add some explanatory text to the message box, explaining what you did
* Click 'Create Pull Request'
* Bask in the glory of helping the Racket Community

# How to contribute once you are more familiar with Racket

* [Tutorial: Contributing to Racket](https://blog.racket-lang.org/2017/09/tutorial-contributing-to-racket.html) (27 Sep 2017) by Ben Greenman

# Ways you can contribute to the Racket ecosystem
* Try a [Project](https://github.com/racket/racket/wiki/Project-Ideas)
  * If you make a library, [publish it](http://docs.racket-lang.org/pkg/getting-started.html), so other Racket users can find it and use it.
  * If you make an app you can use DrRacket [to create an executable you can distribute](https://docs.racket-lang.org/drracket/create-exe.html) or use [Raco to create Stand-Alone Executables](https://docs.racket-lang.org/raco/exe-dist.html)
* Fix a bug: [Easy bugs to fix](https://github.com/racket/racket/wiki/Easy-bugs-to-fix)
* [Extend DrRacket](https://docs.racket-lang.org/drracket/extending-drracket.html) with a [Teachpack](https://docs.racket-lang.org/drracket/extending-drracket.html#%28part._teachpacks%29) or a [Plugin](https://docs.racket-lang.org/tools/index.html)
* [make your own language](https://docs.racket-lang.org/guide/languages.html) (documentation)
  * [beau­ti­ful racket](https://beautifulracket.com) is the best place to start
* [[Integration Projects]] These are improvements to other systems to better support Racket.

## Contribute to the documentation
 * [[Documentation Improvements]] has ideas where you can help improve the documentation

## Guides to contributing to Racket

* [Tutorial: Contributing to Racket](https://blog.racket-lang.org/2017/09/tutorial-contributing-to-racket.html) (27 Sep 2017) by Ben Greenman

See [[Code Improvements]] for a list of tasks. These are improvements to the Racket source.

Older tutorials:
* [Tutorial: Contributing to Racket by Joe Gibbs Politz(2012)](http://blog.racket-lang.org/2012/11/tutorial-contributing-to-racket.html)
* [A guide for infrequent contributors to Racket(2013)](http://www.greghendershott.com/2013/04/a-guide-for-infrequent-contributors-to-racket.html)

Note: some things have changed since these blog posts were written, but they remain mostly accurate; ask on the racket mailing list if you have any questions. (it is a very friendly community)


Also

<http://rosettacode.org/wiki/Reports:Tasks_not_implemented_in_Racket>

