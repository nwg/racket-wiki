This page gives an overview of the Racket release process including its schedule, participants' responsibilities, and rationale. Details on the mechanics of releases are on the [[Release process]] page.

# Executive summary

Commit to git when you want the world to use your code. Update tests and documentation every time that you commit code changes.

A normal release process happens once every three months (January, April, July, and October), with the following schedule:

 * 1st: a reminder is sent out
 * 7th: "branch day" --- the release branch is created
 * 15th: testing begins
 * ~30th: the release is announced and made available on the download page

# What is a normal release?

A **normal release** is a bundle whose version number has no fourth sub-number, and one that we intend for all Racket users to download as soon as it becomes available.

We also have **snapshot builds**. These builds always have a fourth number in their version, and they are built from Git. They are also releases in the sense that we intend for a small (but significant) fraction of Racket users to use daily (more or less). Snapshot builds are available from various [snapshot sites](http://pre.racket-lang.org/).

The quality demands for a normal release are much higher than for a snapshot build, because the audience is much wider. Nevertheless, a snapshot build has quality standards too. Just keep in mind the implication of pushing commits to the repository: it is a signal that someone you don't know should run your code, read your docs, and expect it all to work (but they'll be a little forgiving if it's not quite right today and it's fixed tomorrow).

During periods of major changes, we sometimes have an intermediate level of alpha releases, which have version numbers of the form “X.9Y” or “X.Y.9ZZ”. These releases are used very infrequently, usually before major changes. (The availability and convenience of snapshot builds has diminished the need for such alpha releases.)

# When do we create a normal release?

We create a normal release every three months (currently January, April, July, and October). The three-month schedule is a compromise between allowing improvements to flow into the release continuously versus the effort required for integration and system testing.

We *do not* create a normal release to push out a new feature. If you need a feature included in the normal release by a particular date, then plan ahead and have it ready before the release date. A reminder will be sent a week prior to the branch creation to allow people to prepare for the release in cases like this.

On occasion, a scheduled release may go out with a particularly bad bug that needs to be fixed before the next normal release. Such intermediate releases will be based on a branch from the most recent normal release, and they may not require performing the entire release checklist.

# Why distinguish normal releases from snapshot builds?

As our project has grown, the snapshot builds have been crucial for getting normal releases out on a human timescale. Since lots of people test the most recent code, things mostly work all the time.

Nevertheless, to ensure a quality package for less forgiving users, we need to synchronize the point at which all developers have their most refined efforts in place. A release, then, is a synchronization point for integration and system testing.

Note that the audience for a normal release can be very wide: it includes schools, labs, and people who use 3rd-party packages through their OS.

# What is the relationship between a release and a set of features?

Normal releases are driven by time, not by feature sets. The features of a normal release are frozen once testing begins, shortly after the release branch is created. Adding a feature after [branch day](#branch-day) and asking for it to be merged to it should be rare: doing so means that you're including a relatively unused and untested piece of code with a release, so you should reconsider it an be sure that there is good reason for doing so. Adding a feature after testing has begun requires unanimous approval from [management](#management), and the rules are set up to make such approvals very difficult.

A normal release, then, is unrelated to the pressure for adding features or fixing bugs. This pressure derives from external conditions and constraints, regardless of releases or version numbers: a feature that is useful for a class, your advisor requires that a feature is in publishable condition by some date, a company promises to send you a large check if you add a feature, or if you just want the world to experience your wonderful new invention. Whatever the reason is, you need to manage *your own* schedule to make it to *your own* deadline. (In other words, it should not affect the rest of the project's timeline.) In the absence of any other constraints then, you should not plan in terms of “I want to add feature X, and it should be ready for version Y”. Implement feature X, take however long it takes, and deliver the results to snapshot users as soon as possible.

The set of features in a release as compared to the previous normal release determines the version number: most releases change only the second number of the version. The first version number changes only with major architectural changes that affect the whole system.

# How does release time differ from any other time?

Once the release branch is created ("branch day"), there is a week before testing begins. This should be a time of heightened testing and tweaking. Review code that you own which is now included in the release branch and make sure that it's in good shape (you can ask for it to be retracted if you can't make it complete); take some time to go over your bugs; run your tests to avoid last minute surprises; make sure you use a snapshot build and keep an eye on anything else that looks suspicious (as an extreme example, if you run some code and get a segfault then don't just ignore and run it again). Other than this, you can go about as usual with new developments on the master branch. (Specifically, if you had a feature that you held off because you didn't want it to be included in the release, then now it can be added without affecting the release.)

Note that testing, tweaking, and documentation polishing are *not* release-only tasks; they happen all the time for the snapshot build.

As a branch day approaches, it really isn't a time for making up for months of late work and pushing a lot of new material out. If you have a great new idea, you can still work on it and commit your progress to the master branch, but chances are very low that the idea should be in the release. It's better to let the code mature for a while on the master branch — and have it included in the following release (which will happen soon anyway).

Note that even minor changes can have surprising consequences for a project of PLT's scale. Therefore, once the release branch was created, please keep merge requests to finishing touches and bug fixes only. Seriously.

Sometimes, an existing piece of code isn't quite in place when the release starts — maybe you didn't get to finalize the work in time for the release branch. If it requires more than “finishing touches”, ask to remove it from the release branch, effectively reversing commits that were included in it, or, if possible, provide a minimal patch to disable the new code. This is likely a better option than fixing everything to work in the last minute. If in doubt, raise your concern on the dev list.

# What should individuals do just before a release?

A week before the testing begins, the release branch is created ("branch day"). This is done early for several reasons. The main reason is a strong signal that the release is starting soon — and that you should start preparing for it: review your code and make sure it's in good shape; see that there's no half-made work that is comitted, and if so either finish it as soon as possible, or ask for it to be retracted; run your tests a few times and ask people if they see any problems.

Second, it provides some “buffer time” before testing (and the actual release process) starts for such wrap-up work, in other words, it ensures that the release is a logically coherent piece of work rather than a snapshot of some random moment. As the testing period gets closer, the expectation is for merge requests to dwindle down as the release is getting more stable.

Related to this, it gives you some time to consider changes that you did: are they ready to be included in a public release? Maybe you want to disable the new feature in the release to get some more testing exposure before it becomes more public? Are there any outstanding bugs that you meant to fix but didn't get to?

Finally, all of this can be summarized as a matter of prioritizing. In general, the release process is design to minimize interference with your normal workflow. But in parallel to that, this week is a time to shift your priorities and focus on the upcoming release. Once this is done, all you have left is the testing stage that follows.

# What should individuals do during release time?

If you're on the Release Manager's list to receive reminders when the release process starts — congratulations! However, please keep in mind a few things:

  - They're generally *reminders* to make sure that things don't fall through the cracks, not a request to start working on something. If you're responsible for testing or for some documents, you should be able to quickly respond that everything is fine, because you've been testing or writing all along (and you just checked or proofread one more time for good measure).
  - the Release Manager needs response relatively quickly. Two days should be normal. In bad cases the release process can take a week when unexpected problems arise. If you can't regularly respond on that time scale, then we need someone else to take over your job. If you know you're going to be especially busy near a release (e.g., due to a paper deadline), then don't wait until you get the reminder to say you can't do it; we set a schedule in advance so you can plan around such problems.
  - Even if your tests are checked by drdr or the pkg-build service (which is a very good idea) you should still run them. This is because in some cases there are platform-dependent bugs, or the drdr/pkg-build test suite can miss failures because the tests are not setup correctly (this *has* happened, many times).
  - Keep an eye for any problems, and report anything that looks bad. Don't dismiss potential problems because “they're not your problem”.
  - If for some reason you really need to merge changes that could potentially interact with other parts of the distribution and the changes are merged to the release, then make sure to notify the list, so we can consider another quick round of tests. Note that this would be a very rare situation, since at this point things tend to roll fast and delays are more problematic. In case of doubts, consult with [management](#management).

Otherwise, your help is greatly appreciated in exercising parts of DrRacket that you don't normally use. Note that you should be testing the release branch from the [candidate build](#candidate-builds) — don't check out the release branch. The intention is to try things out under the same conditions as end users.

# Rules for a normal release

## Management

PLT **management** runs the release. Current management is Matthias, Robby, Jay, Sam, Ryan, Vincent, John, and Matthew.

## Schedule

There are four normal releases per year, starting in January, April, July, and October.

Each release has the following schedule:

 * 1st: a reminder is sent out
 * 7th: "branch day" --- the release branch is created
 * 15th: testing begins
 * ~30th: the release is announced and made available on the download page

For each release, a branch is created in the main repository in preparation for the release. The date of branch day is the 7th day of the month. One week before branch day (i.e., on the 1st), the Release Manager will normally send a courtesy reminder of the upcoming branch.

A week after the branch creation (on the 15th), testing begins. This time is relatively firm, and will move only in exceptional cases where more work is needed. (Pending management approval of such an extension.)

## Version Numbers

When a release branch is created, the version number is changed in both the master and the release branches. The release branch version number is not the final one, but instead a release candidate version number (with four parts, where the last one is in the 900s). Examples:

  - for release 5.0, a release candidate might be numbered 4.90.90.900.
  - for release 5.4, a release candidate might numbered be 5.3.90.900.
  - for release 5.4.3, a release candidate might be numbered 5.4.2.900.

In most cases, a release number will have two digits, such as 5.4. If a release is created to simply add a small change, such as a security fix or a documentation note, then it's given a number like 5.4.1. (Release 6.2.1 is an example of this.) A release number that changes the major number, such as 5.0 or 6.0, is used for major changes with significant potential incompatibility, or to indicate a substantial change in Racket as a whole.

## Changing the Release Content

The content of a release is drawn from the main Racket repository as well as all package repositories reachable from the `main-distribution` package. The release contains whatever exists in their master branches on branch day, with adjustments done due to merge requests in the following week before testing begins.

If you happen to commit some changes just before branch day and you don't want them to be included in the release, e-mail the repository's manager with the revision numbers to “unmerge” from the branch.

Otherwise, changes to the branch for the actual release must work towards finalizing code and bug fixes. To make such a change, commit to the master branch and indicate in the commit message that you want it to be merged to the release branch. The preferred method is to include a line saying "Merge to release branch." at the end of the commit message. Failing that, you can also record the commit's SHA1 number and send it to the repository's manager, but the commit message is preferable. When the release branch exists, new release candidate builds will happen from time to time as new commits are merged in.

Note that during the time between the branch creation and the testing, the decision on which commits should be merged is up to you. However, it is expected that you be aware of the situation and commit responsibly as a result: avoid excessively big commits, new features, etc.

Once testing begins, the conceptual cost of additional commits becomes prohibitively steeper, and to get new commits in you have to convince management that it's OK. (For example, it should be considered as possible grounds for a new round of testing.) You and management should agree on which member of management is most qualified to read and evaluate your commit; they will decide if it is included or not.

Past experience suggests that management will be picky about new commits. If possible, design your commit to be as simple and focused as possible (even if this means you make a different commit for the fix on master). New features are very unlikely to be approved.

Details about working with release branches are at [[Release process]]. Repository managers are listed at [[Release repo managers]].

## Candidate Builds

**Candidate builds** are created from the branch and announced on the dev list. Such builds are available at a location separate from the usual snapshot builds (to avoid using it by mistake). Sometimes these builds will also be announced on the general users mailing list, when we want to solicit even wider testing. Candidate builds are triggered manually once the release branch is made, and refreshed once enough commits are merged. A fresh updated build is ready before testing begins.

## Testing Checklist

A week after branch day, the Release Manager sends out a link to the testing checklist. Each checklist item has a specific person attached to it, and that person is responsible for completing the task within a few days that the checklist goes out (usually 2-3 days, at most a week).

Use the [candidate build](#candidate-builds) for checklist processing, not your git clone. It's good to try out building the release branch, but for testing, use the provided builds.

Any issues that are found (in testing or otherwise) are added to the checklist, and block the release; the release cannot proceed unless all tests are done, and all blocker issues are resolved.

## From Candidate to Release

The time between the testing start date and the release date is used for extra testing, bug fixes, and release-checklist tasks. Checklist tasks will generally require a total of a week (so releases are usually announced around the 23rd), but the actual delay is determined by management for each release.

When the checklist is completed, an announcement message is composed, and the version number in the release branch is changed from the [release candidate number](#version-numbers) to the final number. Finally, the release is made publicly available.

Once testing begins, management is expected to review each failure that occurs in DrDr for the release branch. One member of management will be designated for each failure and is expected to report back to the rest of management what, if anything, should be done.

To facilitate this review process and generally to keep an open channel of communication, management is expected to meet every other day (via Skype or in person) to discuss the release.

## Senior Mangement

When something goes wrong with the release process (as it inevitably does) and people get too excited (as happens a bit more than we wish it did), it is senior management's job to step in, preferably in consultation with some subset of the management. Senior management should just lay down the law: do this and we get the current release back on track. When this happens, the rest of the management's job is to just do what is said with a minimum of fuss.

We imagine this power being used infrequently, and always with the limited scope of getting the current release process back on track. If this power is abused, we will discuss it, but only after the release, not before.

Current senior management is Matthias.
