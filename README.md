# Contributing guidelines
Common guidelines for contributing to d2si-oss projects

## TL;DR
We want to make contributing straighforward and easy for everyone. As such and
unless otherwise stated we are following the
[GitHub flow](https://guides.github.com/introduction/flow): any commit must be
made to a topic branch in a local fork and submitted via a pull request before
it can can be merged.  
If you are familiar with GitHub (and Git), branching and opening a pull request
or an issue... then you should be able to start contributing right away.

**Contributors must agree to the following:**
- material without explicit copyright assignment will be assigned to
[D2SI](http://d2-si.eu)
- apart from a few identified exceptions, material must be licensed under the
[ISC license](https://opensource.org/licenses/isc-license.txt)

D2SI staff should also be aware of
[additional guidelines](#additional-guidelines-for-d2si-staff).

## Table of contents

  * [Coding style](#coding-style)

  * [Documentation](#documentation)

  * [Git](#git)
    * [Workflow](#git-workflow)
    * [Syncing a fork with its upstream](#syncing-a-fork-with-its-upstream)

  * [Additional guidelines for D2SI staff](#additional-guidelines-for-d2si-staff)
    * [The d2si-oss core team](#the-d2si-core-team)
    * [Organization members](#organization-members)
    * [Organization owners](#organization-owners)
      * [Creating a new repository](#creating-a-new-repository)
      * [Forking an upstream repository](#forking-an-upstream-repository)

## Coding style

We love punch cards, so the maximum line width is 80 characters.
For regular text (i.e. not code), the fmt(1) utility can be used:

```bash
fmt -w 80 /path/to/file
```

We usually do not want to enforce a particular style because we intend to host
a lot of different projects by a lot of people with different background. That
said we do request style consistency within the same project (this is
especially important for reusable recipes like ansible roles and terraform
modules).

Here's a non exhaustive list of code style helpers that we find useful.

| Language / Tool | Linter / Formatter          |
|-----------------|-----------------------------|
| Ansible         | ansible-lint                |
| Go              | Native Linter (compilation) |
| JSON            | JsonLint                    |
| PHP             | PHP-CS-Fixer                |
| Python          | PEP 8                       |
| Terraform (HCL) | terraform fmt               |

## Documentation

Substential contribution must always come with exhaustive documentation. We
consider documentation as important as code.

## Git

The **master** branch should be considered as a production|deploy branch.

### Workflow

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
See [GitHub Help](https://help.github.com/articles/syncing-a-fork)
for more information.

## Additional guidelines for D2SI staff

Anyone from D2SI staff willing to setup a new project can ask one of the
organisation owners to create a repository which he will be the owner and
responsible of the contributing workflow like answering issues, reviewing and
merging pull requests, etc.

### The d2si-oss core team

By default, members of the core team watch and have admin rights over all
projects and hence can handle the global contributions workflow.

### Organization members

There won't be any organization members besides the owners and members of the
core team and the default configuration (right etc.) will not be modified.  
That also means that if a user leaves the core team, he must be removed from the
organization members list.

### Organization owners

Organization owners have full control over the d2si-oss organization and are the
only one with repository creation rights.  
They can also dismiss the requirement of opening a pull request to commit
something but that is only done on rare exceptions.

#### Creating a new repository

Note that status checks (Travis etc.) are not a requirement.

1. Go to the top level URL of the
  [d2si-oss organization](https://github.com/d2si-oss)

2. Click on [**New**] then:
   * Make sure the **Owner** is set to d2si-oss
   * Give it a meaningful **Repository name** and **Description**
   * Check the **Initialize this repository with a README** box and click on
    [**Create repository**]

3. Click on **Add topics** and add a few descriptive tags then click on
   [**Done**].

4. Go to **Settings** and uncheck the **Wikis** box

5. Go to the **Collaborators & teams** tab then:
   * Add **core** to the **Teams** list and give it **Write** access
   * Add the project submitter username to the **Collaborators** list and give
     him/her **Write** access (even if the submitter is already a member/owner
     of the d2si-oss organization or the core team because he may leave the orga
     at some point)

6. Go to the **Branches** tab and select **master** under the **Protected
   branches** section

7. Check **Protect this branch** and **Require pull request reviews before
   merging** boxes then [**Save changes**]

8. Add the default [LICENSE](templates/LICENSE) and
   [CONTRIBUTING.md](templates/CONTRIBUTING.md) files to the repository

#### Forking an upstream repository

1. [Fork](https://help.github.com/articles/fork-a-repo) the repository

2. Uncheck the **Wikis** box

3. Go to the **Collaborators & teams** tab then:
   * Add **core** to the **Teams** list and give it **Write** access
   * Make sure the **Collaborators** list is empty
