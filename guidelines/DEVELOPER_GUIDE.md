# Developer Guidelines

## Repository structure

Create repositories with a clear scope and README to document the purpose of the code inside. 

Repository names should be lower-kebab-case and uniquely descriptive (e.g., `pytorch-controller-implementations`, `nvidia-usd-tools`).

Repositories should be private by default, unless the work is a fork of an existing open-source project or if the consortium members have agreed to open-source the work under a specific license.

## Branch and Pull Request workflow

The default branch on all repositories should be `main`. Branch protection rules should prevent developers from pushing directly to `main`. Instead, a Pull Request should be opened from a relevant feature branch (e.g., `feature/algorithm-implementation`, `fix/division-by-zero`).

For each package affected in the change, document the changes in the CHANGELOG.md file of the respective package, following the [CHANGELOG style guide](./CHANGELOG_STYLE_GUIDE.md). Do not change the version of the package(s) unless you intend to make a release (see the [](./) workflow section).

PRs into `main` should be closed with the **squash** strategy to create a single commit on `main`. When squashing a PR, the commit subject and body should be rewritten according to the commit message format rules (see the [commit message format](./COMMIT_STYLE_GUIDE.md) section).

The only exception to the squash rule is when a series of PRs have been closed into a staging branch instead of `main`. Provided that each commit in the staging branch follows the commit message format rules, the staging branch can be fast-forwarded onto `main`.

## Versioning and Release workflow

A package shall be released whenever the version of that package is changed on the `main` branch.

To make a release, a PR should update the package version and package changelog in the respective manifest and CHANGELOG.md files. This can be done from a dedicated release branch (e.g., `release/v1.2.0`) or directly as part of an existing feature or fix PR. If a commit only changes the version and changelog for a release and makes no other changes, then the `release:` commit type should be used.

If the release contains only fixes, the patch version number should be incremented. If the release contains any new features, the minor version number should be incremented. If the release contains any breaking changes to the package, the major version number should be incremented.

The change entries in the “Upcoming changes” section of the changelog should be rewritten into clear release notes under a new heading matching the new version number (see the example in the Changelog example section). Strongly consider how the new version is changed with respect to the previous release, and amend / rewrite the release notes from the changelog entries accordingly.

Once the package version on the `main` branch has been updated, [create a new Release and associated release tag using the GitHub UI](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository#creating-a-release). Write descriptive release notes using the package CHANGELOG as reference.

For single-package repositories, the release name should be formatted as `Version x.y.z` and the corresponding release tag should always be formatted with the `v` version prefix (e.g., `v0.1.0`, `v2.3.0`). For repositories containing multiple packages that may each have different versions respectively, the release name should include the package name, and the release tag should also be prefixed with the package name (e.g., `package_foo_v0.1.0`, `package_bar_v2.3.0`).

## Code Style

Python code should be formatted according to PEP8.

C++ code should follow the [C++ style guide](./CPP_STYLE_GUIDE.md), which includes references for auto-formatting in VS Code or CLion.
