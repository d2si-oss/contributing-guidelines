# Contributing guidelines
Common guidelines for contributing to d2si-oss projects

## Foreword
First off, thank you for taking the time to contribute!  
It's worth mentioning that the purpose of this document is to provide you with a
set of general guidelines and not strict rules: nothing is set in stone and we
welcome contributions about these contributing guidelines as well :-)

## TL;DR
We want to make contributing straighforward and easy for everyone. As such and
unless otherwise stated we will use the traditional GitHub fork and pull
workflow: any commit must be made to a feature/topic branch in a local fork and
submitted via a pull request before it can can be merged. If you are familiar
with GitHub (and Git), branching and opening a pull request or an issue... then
you should be able to start contributing right away.  
It is **strongly advised** to contact the project owner(s) **before** working on
implementing a new feature or making any kind of large code refactoring.

**Contributors must agree to the following:**
- material without explicit copyright assignment will be assigned to
[D2SI](http://d2-si.eu)
- apart from a few identified exceptions, material must be licensed under the
[ISC license](https://opensource.org/licenses/isc-license.txt); in all cases, a
**license is mandatory**.

D2SI staff should also be aware of
[additional guidelines](#additional-guidelines-for-d2si-staff).

## Table of contents

  * [Coding style](#coding-style)

  * [Documentation](#documentation)

  * [Git](#git)
    * [Workflow](#git-workflow)
    * [Syncing a fork with its upstream](#syncing-a-fork-with-its-upstream)

  * [Issues](#issues)

  * [Additional guidelines for D2SI staff](#additional-guidelines-for-d2si-staff)
    * [The d2si-oss core team](#the-d2si-core-team)
    * [Organization members](#organization-members)
    * [Organization owners](#organization-owners)
      * [Creating a new repository](#creating-a-new-repository)
        * [Naming conventions](#naming-conventions)
      * [Forking an upstream repository](#forking-an-upstream-repository)
    * [Technical blog](#technical-blog)

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

Make sure you have a [GitHub account](https://github.com/signup/free).  
The **master** branch should be considered as the production/deploy branch.

### Workflow

Extensive information can be found in this excellent
[forking workflow tutorial](https://www.atlassian.com/git/tutorials/comparing-workflows#forking-workflow).

In a nutshell:

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

3. Commit the changes in logical and incremental chunks and use
   [interactive rebase](https://help.github.com/articles/about-git-rebase)
   when needed.  
   In your
   [commit messages](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html),
   make sure to:
   * use the present tense
   * use the imperative mood
   * limit the first line to 72 characters
   * reference any associated issues and/or PRs (if applicable)

   ```bash
   git commit -am 'Add new feature...'
   ```

4. Push the topic branch to the remote forked repository.

   ```bash
   git push origin ${TOPIC_BRANCH}
   ```

5. [Open a Pull Request](https://help.github.com/articles/about-pull-requests)
   with a clear title and description.

6. Once the PR has been merged, the topic branch can be removed from the local
   fork.

   ```bash
   git branch -d ${TOPIC_BRANCH}
   git push origin --delete ${TOPIC_BRANCH}
   ```

### Syncing a fork with its upstream

This is used to keep a local fork up-to-date with the original upstream
repository.

1. Connect the local to the original upstream repository.

   ```bash
   git remote add upstream https://github.com/d2si-oss/${REPONAME}
   ```

2. Checkout, fetch and merge the upstream master branch to the local one.

   ```bash
   git checkout master
   git fetch upstream
   git merge upstream/master
   ```

3. Push changes to update to remote forked repository.
    ```bash
    git push
    ```

See [GitHub Help](https://help.github.com/articles/syncing-a-fork)
for more information.

## Issues

If you find a bug that you don't know how to fix, please
[create an issue](https://guides.github.com/features/issues/):
* use a clear and descriptive title
* give a step by step explanation on how to reproduce the problem
* include as many details as possible, even ones that may seem irrelevant;
  [gists](https://help.github.com/articles/about-gists/) are a good way to
  include large amount of context and information
* describe what was already tried to fix the problem

## Additional guidelines for D2SI staff

Anyone from D2SI staff willing to setup a new project can ask one of the
organisation owners to create a repository which (s)he will be the owner and
responsible of the contributing workflow like answering issues, reviewing and
merging pull requests, etc.

### The d2si-oss core team

By default, members of the core team watch and have admin rights over all
projects and hence can handle the global contributions workflow.

### Organization members

There won't be any organization members besides the owners and members of the
core team and the default configuration (right etc.) will not be modified.  
That also means that if a user leaves the core team, (s)he must be removed from
the organization members list (i.e. orga members and core team members must stay
in sync).

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
   * Give it a meaningful [**Repository name**](#naming-conventions) and **Description**
   * Check the **Initialize this repository with a README** box and click on
    [**Create repository**]

3. Click on **Add topics** and add a few descriptive tags then click on
   [**Done**].

4. Go to **Settings** and uncheck the **Wikis** box

5. Go to the **Collaborators & teams** tab then:
   * Add **core** to the **Teams** list and give it **Admin** access
   * Add the project submitter username to the **Collaborators** list and give
     him/her **Admin** access (even if the submitter is already a member/owner
     of the d2si-oss organization or the core team because (s)he may leave the
     orga at some point)

6. Go to the **Branches** tab and select **master** under the **Protected
   branches** section

7. Check **Protect this branch** then [**Save changes**]

8. Add the default [LICENSE](templates/LICENSE) and
   [CONTRIBUTING.md](templates/CONTRIBUTING.md) files to the repository

##### Naming conventions

There are multiple types of repositories.

| Type                           | Convention            | Example                 |
|--------------------------------|-----------------------|-------------------------|
| wrapped up solution (use case) | demo-vendor-tech-name | demo-aws-lambda-foobar  |
| generic reusable recipes       | tech-type             | ansible-roles           |
| software                       | software name         | superduperutility       |
| organizational repo            | self-explanatory      | contributing-guidelines |
| forked repositories            | none                  | terraform               |

#### Forking an upstream repository

1. [Fork](https://help.github.com/articles/fork-a-repo) the repository

2. Uncheck the **Wikis** box

3. Go to the **Collaborators & teams** tab then:
   * Add **core** to the **Teams** list and give it **Admin** access
   * Make sure the **Collaborators** list is empty

Regularly keep the forked repository up-to-date with its upstream: see
[Syncing a fork with its upstream](#syncing-a-fork-with-its-upstream) for
details.

### Technical blog

Anyone can submit an article for the [techblog](http://techblog.d2-si.eu/), just
get in touch with someone from the d2si-oss core team. Refer to the
[GitHub Help](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/#platform-linux)
to set up a local version of the Jekyll GitHub Pages to make it easier to test
changes without the need to publish them first.
