# git-flow-sandbox

## Installation

Install `git flow` using the following command.

```sh
brew install git-flow
```
```sh
sudo apt-get install git-flow
```

## Initialization

In order to use `git flow` in your repository, you must first initialize it. This is required for every development environment.

```sh
git flow init
```

Set the following during initialization:

```sh
Branch name for production releases:
> staging

Branch name for "next release" development:
> dev

Feature branches? [feature/]
> n/a (default)

Release branches? [release/]
> n/a (default)

Hotfix branches? [hotfix/]
> n/a (default)

Support branches [support/]
> n/a (default)

Version tag prefix []
> n/a (default)
```

## Feature Development
1. Start a feature branch.

```sh
git flow feature start feature-name
```

2. Develop, commit, push, and create a PR.

> [!NOTE] You may also use `git flow feature publish feature-branch` to push the local feature branch to the remote repository.


3. Once the PR is reviewed and approved, merge to `dev`.

> [!WARNING] Running `git flow feature finish feature-branch` will merge the feature branch **without** creating a pull request, so avoid using it.

## Release

### Dev → Staging

1. Ensure that the local branches are updated.

```sh
git pull --all
```

2. Start a release branch.

```sh
git flow release start release-version
```

2. Make final changes, such as updating versions, and commit.

3. Finish the release

```sh
git flow release finish release-version
```

4. Push updates to remote

```sh
git push origin staging dev --tags
```

5. On GitHub, create a release from the created tag.
6. Select the created tag, then generate the release notes.
7. Check "Set as a pre-release". 
8. Publish release.
9. Approve workflow run.
10. Verify deployment on staging.

### Staging → Production

1. Merge staging into main.

```sh
git checkout main
git pull                     # Ensure that main is up-to-date
git merge --ff-only staging  # Include tag set in staging release
git push origin main --tags
```

2. On GitHub, update the release to a full release (uncheck "Set as a pre-release").
3. Approve workflow run.
4. Verify deployment on production.
