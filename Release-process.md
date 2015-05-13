This is a description of the current (post-split) release process.

# Goals

 - I (Ryan) can build the release.

 - Everyone else can build the release too (eg for testing).

 - Anyone can retrieve old release sources (eg, "recreate release 5.2").

The first two are important. We could live without the third, but it
would be nice to have, and if we don't support it now it becomes
harder later on.


# Process Overview

The main repo has a short-lived release branch (and a long-lived
stable branch), as it does now. The release branch creation time stays
the same. I manage the main release branch (cherry-picking commits)
just as before.

Each pkg repo **may** have a (short-lived) release branch, but pkg
release branches are created only when needed. For a given pkg, the
code that gets included in the release is determined by the following
rules:

- If the pkg repo has a release branch, it's the contents of the
  release branch (when the repo is polled for a build).

- Otherwise, it's the **snapshot** of the master branch when the
  release catalog was created (which I'll call "branch day"). It does
  **not** track later updates to the master branch.

When a pkg release branch is needed, it is created and managed by the
pkg repo manager. (Note: one per repo, not per pkg.) The pkg repo
manager is responsible for making sure their release branch is
updated; they may set policy on who can update it. (Enforcement is
probably either not possible or not feasible.) For example, let's say
Sam is responsible for the TR repo. Sam may allow Vincent and Asumu to
update the TR repo's release branch (eg by cherry-picking commits from
master), but Sam should be vetting the changes locally and keeping
things from falling through the cracks.

The current list of pkg repo managers is at [[Release repo managers]].

A pkg repo release branch should be updated only by cherry-picking
commits from another branch (usually master). 
In extraordinary situations, the release branch may be updated
directly, but the committer should explain in the commit message why a
direct update is necessary.

Release management should watch all commits (especially late-stage
commits) to pkg repo release branches.

I create a release catalog like the standard catalog, trimmed to
main-distribution, but pointing to either the branch-day master commit
or the release branche for each pkg repo. I commit the release catalog
to [the racket/release-catalog
repo](https://github.com/racket/release-catalog).

I periodically update the release catalog by polling for new or
updated pkg repo release branches. Consequently, an update to a pkg
repo release branch is automatically incorporated into future release
builds without additional intervention or review.

At the end of the release process, I create a "v$VERSION" tag in all
pkg repos with release branches (to prevent the commits from being
GC'd) pointing to the current release branch state and then delete all
pkg repo release branches. Pkg repos still pointing to their
branch-day master commits do not get tags.


# Instructions for developers

Commit to master as normal.

If a commit should be included in the release (in the main repo or in
a pkg repo), include the sentence "Merge to release branch." at the
end of the commit message on a separate line.

Alternatively (if you forget about marking the commit until after
you've pushed it), email the pkg repo manager with the list of SHA1
hashes of the commits to include. I recommend forwarding the push
acknowledgement email, since it often contains a summary of the
changes, which makes the request easier to review.

The current list of pkg repo managers is at [[Release repo managers]].


# Instructions for pkg repo managers

## Determining a pkg repo's current release state

Use the following command to determine whether a pkg repo has a
release branch or, if not, to find the the branch-day master commit:

    raco pkg catalog-show --catalog https://raw.github.com/racket/release-catalog/master/release-catalog/ <pkg-name>

If the "Source" field's URL ends in "#release", the pkg is set to a
release branch. Otherwise it is using the branch-day snapshot of the
master branch (or the release catalog hasn't been updated since the
creation of the release branch).

If the pkg is using the branch-day master snapshot, then the
"Checksum" field contains that commit's SHA hash. Use that commit when
creating a new release branch (see below).

## Creating the release branch

First, make sure you're up to date:

    git pull

If a stale release branch exists from a previous release cycle, delete
it:

    # List local branches
    git branch
    # If a release branch exists, delete it
    git branch -D release

To create the release branch as a copy of the branch-day master
snapshot:

    # let CHECKSUM be the Checksum of the pkg in the release catalog (see above)
    git checkout -b release <CHECKSUM>
    git push origin release

Alternatively, to create the release branch as a copy of the *current*
master branch:

    git checkout -b release master
    git push origin release

I recommend switching back to the master branch at the end of updating
the release branch to avoid accidentally committing directly to the
release branch.

## Updating the release branch

To see the sequence of commits in master since its common ancestor
with release, annotated with whether they've been cherry-picked to the
release branch, use the following command:

    git log --reverse --cherry release...master

To update the release branch:

First, make sure your checkout of the pkg repo is up to date.

To "fast-forward" the release branch up to a certain commit on master,
use the following commands:

    # Switch to the release branch
    git checkout release
    # Fast-forward the release branch to <commit-hash>
    git merge --ff-only <commit-hash>

To include a single commit in the release branch, do the following:

    # Switch to the release branch
    git checkout release
    # Cherry-pick the commit
    git cherry-pick -x <commit-hash>

When including more than one commit, I recommend picking them one at a
time in the same order they appear in the master branch.

If it applied cleanly, then push and switch back to the master branch:

    git push
    git checkout master

If the commit doesn't apply cleanly, check whether the commit
changes a region of code previously changed by an unpicked commit
and consider whether the previous commit should be picked first.

If not, then you can try manually fixing the merge conflict.

I recommend configuring git with the following command:

    git config merge.conflictstyle diff3

which results in conflicts being marked in the following format:

    unchanged text
    <<<<<<< HEAD
    text from master
    ||||||| parent of <commit to include> <commit msg summary>
    text from the common ancestor of master and <commit to include>
    =======
    text from <commit to include>
    >>>>>>> <commit to include> <commit msg summary>
    unchanged text

That is, the text in the common ancestor has undergone two conflicting
changes in different branches. Your goal is to replace the whole
bracketed area with a version of the text that incorporates both
changes.

If you can't resolve the merge conflict, ask me for help.
