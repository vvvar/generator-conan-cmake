# generator-cpp-github

Yeoman-based, GitHub-ready generator of cross-platform C++ apps and libraries with VS Code integration.

## Motivation

I like trying new ideas with C++. Setting up a new C++ project for me is so time-consuming that I often find myself spending more time configuring it than actually coding. On top of that, I tend to skip quality tools such as unit testing, SCA and linting in the early stages and then suffer to make them work on an already-existing code base.
To address all that, I've made this generator. Primary for myself. With technologies that I am often using. With structure that makes sense best to me. Then I thought it could be useful for somebody. So here it is.

## Philosophy

- Use existing open-source tools as much as possible. Minimize custom solutions
- Prefer tools that are easy to set up over highly-customizable complex tools
- Prefer cross-toolchain tools over toolchain-specific solutions. Example - SonarLint over clang-tidy
- The project is as self-contained as possible. If something is needed to be installed/configured by the developer - there should be a task to do it within the project. Exception - task runner itself and basics
- Everything should be usable from the local machine. No "CI-specific" solutions. Local ease of use is a priority
- Thin CI-integration. CI just executes the same tasks that the developer can execute locally
- Latest C++ standard
- Code-style is enforced
- Unit-testing is enforced
- Maximum possible SCA and linter strictness is enforced
- Dependencies should be versioned(where possible)
- If something is unused then it should be removed
- VS Code is the editor of choice. However, editor-independent solutions are preferred 
- You should be able to build, test, debug and analyze the project without the editor. CLI solutions are preferred
- macOS, Linux and Windows are the target platforms 
- [Trunk-based development](https://trunkbaseddevelopment.com)
- Forbid merge into the `main` unless PR passed all quality checks on a CI
- Squash merge strategy. Every commit in the `main` is self-contained 
- Every commit in the `main` branch is a release candidate
- Every commit in the `main` branch has the unique version

## Tech Stack

- [just](https://github.com/casey/just)
- [Conan 2.0](https://docs.conan.io/2/)
- [CMake](https://cmake.org) + [ccache](https://ccache.dev) + [Ninja](https://ninja-build.org)(on all platforms)
- [GoogleTest](https://github.com/google/googletest)
- [clang-format](https://clang.llvm.org/docs/ClangFormat.html)
- [Sonar Lint](https://www.sonarsource.com/products/sonarlint)
- [Python 3](https://www.python.org) + [black](https://black.readthedocs.io/en/stable/)
- [Homebrew](https://brew.sh), [Chocolatey](https://chocolatey.org) and [Apt](https://wiki.debian.org/Apt)
- [GitHub Action](https://docs.github.com/en/actions)
- [Docker](https://www.docker.com)
- [VS Code](https://code.visualstudio.com) + [Grammarly](https://marketplace.visualstudio.com/items?itemName=znck.grammarly) + [CodeWhisper](https://aws.amazon.com/codewhisperer/)

## Installation

1. Install [`nodejs`](https://nodejs.org/en)
2. Install [`Yeoman`](https://yeoman.io)
```sh
npm install -g yo
```
3. Clone this repo
4. Add this generator
```sh
cd /path/to/cloned/repo
npm install
npm link
```

## Usage

### Generate C++ Library project

```sh
yo cppgen:cpplib
```

### Generate C++ Application project

```sh
yo cppgen:cppapp
```

[Example](https://github.com/vvvar/yo-cppgen-example-app)

### Validate project folder structure

```sh
yo cppgen:[type] --validate
```