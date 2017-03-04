# Contributing guidelines
Common guidelines for contributing to d2si-oss projects

## Git worflow

1. [Fork](https://help.github.com/articles/fork-a-repo) and clone the
repository you want to contribute to:

```bash
git clone https://github.com/${USERNAME}/${REPONAME}
cd ${REPONAME}
```

2. Create a feature
[branch](https://help.github.com/articles/creating-and-deleting-branches-within-your-repository)
where you will add and commit your changes:

```bash
git checkout -b my-new-feature
```

3. Commit your changes in logical and incremental chunks.
Refer to these
[git commit message guidelines](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
and don't hesitate to use
[interactive rebase](https://help.github.com/articles/about-git-rebase)
when needed.

```bash
git commit -am 'Add new feature...'
```

4. Push the branch

```bash
git push origin my-new-feature
```

5. [Open a Pull Request](https://help.github.com/articles/about-pull-requests)
with a clear title and description.
