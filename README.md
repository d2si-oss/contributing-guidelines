# Contributing guidelines
Common guidelines for contributing to d2si-oss projects

**By contributing, you agree to the following:**
- material without explicit copyright assignment will be assigned to
[D2SI](http://d2-si.eu)
- apart from a few identified exceptions, material must be licensed under the
[ISC license](https://opensource.org/licenses/isc-license.txt)

## Table of contents

  * [Git](#git)
    * [Git workflow](#git-workflow)
    * [Syncing a fork with its upstream](#syncing-a-fork-with-its-upstream)

  * [Members additional guidelines](#members-additional-guidelines)

## Git

### Git workflow

1. [Fork](https://help.github.com/articles/fork-a-repo) the repository and clone
   it locally.

   ```bash
   git clone https://github.com/${USERNAME}/${REPONAME}
   cd ${REPONAME}
   ```

2. Create a topic branch where changes will be done.

   ```bash
   git checkout -b ${TOPIC_BRANCH}
   ```

3. Commit the changes in logical and incremental chunks.
   Refer to these
   [git commit message guidelines](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
   and use
   [interactive rebase](https://help.github.com/articles/about-git-rebase)
   when needed.

   ```bash
   git commit -am 'Add new feature...'
   ```

4. Push the topic branch to the remote forked repository.

   ```bash
   git push origin ${TOPIC_BRANCH}
   ```

5. [Open a Pull Request](https://help.github.com/articles/about-pull-requests)
   with a clear title and description.

### Syncing a fork with its upstream

This is used to keep a local fork up-to-date with the original upstream
repository.

1. Connect the local to the original upstream repository.

   ```bash
   git remote add upstream https://github.com/d2si-oss/${REPONAME}
   ```

2. Checkout and pull from the master branch.

   ```bash
   git remote add upstream https://github.com/d2si-oss/${REPONAME}
   git checkout master
   git fetch upstream
   git merge upstream/master
   ```

Changes can then be pushed to the remote fork on GitHub.
