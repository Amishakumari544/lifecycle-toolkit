# Contributing to the Keptn Lifecycle Toolkit

We are thrilled to have you join us as a contributor!
The Keptn Lifecycle Toolkit is a community-driven project and we greatly value collaboration.
There are various ways to contribute to the Lifecycle Toolkit, and all contributions are highly valued.
Please, explore the options below to learn more about how you can contribute.


# Before you get started

## Code of Conduct

Please make sure to read and observe our [Code of Conduct](https://github.com/keptn/.github/blob/main/CODE_OF_CONDUCT.md).


* **Create an issue**: If you have noticed a bug, want to contribute features, or simply ask a question that for whatever reason you do not want to ask in the [Keptn Slack workspace](https://slack.keptn.sh), please [search the issue tracker](https://github.com/keptn/lifecycle-toolkit/issues?q=something) to see if someone else in the community has already created a ticket. If not, go ahead and [create an issue](https://github.com/keptn/lifecycle-toolkit/issues/new).

* **Start contributing**: We also have a list of [good first issues](https://github.com/keptn/lifecycle-toolkit/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22). If you want to work on it, just post a comment on the issue.

* **Add yourself**: Add yourself to the [list of contributors](CONTRIBUTORS.md) along with your first pull request.

This document lays out how to get you started in contributing to Keptn Lifecycle Toolkit, so please read on.

## How to Start?

If you are worried or don’t know where to start, check out our next section explaining what kind of help we could use and where can you get involved. You can reach out with questions to [keptn](https://slack.keptn.sh) on Slack.
You can also submit an issue, and a maintainer can guide you!

### Prerequisites

- [**Docker**](https://docs.docker.com/get-docker/): a tool for containerization, which allows software applications to run in isolated environments and makes it easier to deploy and manage them.
- A Kubernetes `cluster >= Kubernetes 1.24` .If you don’t have one, we recommend Kubernetes-in-Docker(kind) to set up your local development environment.
- [**kubectl**](https://kubernetes.io/docs/tasks/tools/): a command-line interface tool used for deploying and managing applications on Kubernetes clusters. 
- [**kustomize**](https://kustomize.io/): a tool used for customizing Kubernetes resource configurations and generating manifests.
- [**Helm**](https://helm.sh/): a package manager for Kubernetes that simplifies the deployment and management of applications on a Kubernetes cluster.

### Linters requirements

This project uses a set of linters to ensure good code quality.
In order to make proper use of those linters inside an IDE, the following configuration is required.

Further information can also be found in
the [`golangci-lint` documentation](https://golangci-lint.run/usage/integrations/).

### Visual Studio Code

In Visual Studio Code the [Golang](https://marketplace.visualstudio.com/items?itemName=aldijav.golangwithdidi)
extension is required.

Adding the following lines to the `Golang` extension configuration file enables all linters used in this project.

```json
"go.lintTool": {
 "type": "string",
 "default": "golangci-lint",
 "description": "GolangGCI Linter",
 "scope": "resource",
 "enum": [
  "golangci-lint",
 ]
},
"go.lintFlags": {
 "type": "array",
 "items": {
  "type": "string"
 },
 "default": ["--fast", "--fix"],
 "description": "Flags to pass to GCI Linter",
 "scope": "resource"
},
```

### GoLand / IntelliJ requirements

- Install either the **GoLand** or **IntelliJ**  Integrated Development Environment (IDE) for the Go programming language, plus the [Go Linter](https://plugins.jetbrains.com/plugin/12496-go-linter) plugin.

- The plugin can be installed via `Settings` >> `Plugins` >> `Marketplace`, search for `Go Linter` and install it.
Once installed, make sure that the plugin is using the `.golangci.yml` file from the root directory.

- The configuration of `Go Linter` can be found in the `Tools` section of the settings.

If you are on Windows, you need to install **make** for the above process to complete.

( **NOTE**: When using the make command on Windows, you may receive an `unrecognized command` error for a command that is installed.
This usually indicates that `PATH` for the binary is not set correctly).

## Submit a Pull Request 🚀

At this point, you should switch back to the `main` branch in your repository, and make sure it is up to date with `main` branch of Keptn:

```bash
git remote add upstream https://github.com/keptn/lifecycle-toolkit.git
git checkout main
git pull upstream main
```

Then update your feature branch from your local copy of `main` and push it:

```bash
git checkout feature/123/foo
git rebase main
git push --set-upstream origin feature/123/foo
```

**All PRs must include a commit message with a description of the changes made!**


### Commit Types

`Type` can be:

- `feat    `: A new feature
- `fix     `: A bug fix
- `build   `: Changes that affect the build system or external dependencies
- `chore   `: Other changes that don't modify source or test files
- `ci      `: Changes to our CI configuration files and scripts
- `docs    `: Documentation only changes
- `perf    `: A code change that improves performance
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `revert  `: Reverts a previous commit
- `style   `: Changes that do not affect the meaning of the code
- `test    `: Adding missing tests or correcting existing tests


## Auto signoff commit messages

We have a DCO check that runs on every PR to verify that the commit has been signed off.

To sign off the last commit you made, you can use
```bash
git commit --amend --signoff
```

or the command below to sign off the last 2 commits you made
```bash
git rebase HEAD~2 --signoff
```

This process is sometimes inconvenient but you can automate it
by creating a pre-commit git hook as follows:
1. Create the hook:
``` bash
touch .git/hooks/prepare-commit-msg
```

1. Add the following to the `prepare-commit-msg` file:
```bash
SOB=$(git var GIT_AUTHOR_IDENT | sed -n 's/^\(.*>\).*$/Signed-off-by: \1/p')
grep -qs "^$SOB" "$1" || echo "$SOB" >> "$1"
```

1. Give it execution permissions by calling:
```bash
chmod +x ./.git/hooks/prepare-commit-msg
```


