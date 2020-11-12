
# Agoric's Typescript Fork

NOTE: This fork is not fully functional.  Notably, the rewriting of tildot (`~.`) is incorrect and its Promises don't have autocompletion.

That being said, you can use this fork to make VSCode understand tildot enough so that your code won't show parse errors.  Other editors that use the Typescript Language Server also should work.

## VSCode

Here are the easiest instructions for installing `@agoric/typescript` in VSCode.  Variants of these instructions will work, but are unsupported.

1. Install this package globally: `npm install -g @agoric/typescript`.
2. Get the path to its installed directory:
```sh
npm list -g @agoric/typescript
/Users/michael/.nvm/versions/node/v12.11.1/lib
└── @agoric/typescript@3.8.0 
```
(thus the path is `/Users/michael/.nvm/versions/node/v12.11.1/lib/node_modules/@agoric/typescript`).  You can verify this directory by listing the `lib/tsserver.js` file within it:
```sh
ls -l /Users/michael/.nvm/versions/node/v12.11.1/lib/node_modules/\@agoric/typescript/lib/tsserver.js 
-rw-r--r--  1 michael  staff  8353156 Oct 26  1985 /Users/michael/.nvm/versions/node/v12.11.1/lib/node_modules/@agoric/typescript/lib/tsserver.js
```
2. Go to `File > Preferences > Settings` or `Code > Preferences > Settings`.
3. Pick the User settings tab.
4. Search for `tsdk` in the search bar.
5. Click `Edit in settings.json`.
6. Add the following setting (pointing to the installed directory containing `tsserver.js`):
```js
{
  "typescript.tsdk": "/Users/michael/.nvm/versions/node/v12.11.1/lib/node_modules/@agoric/typescript/lib"
}
```

After that, your opened Javascript/TypeScript sources will understand tildot.

If they still show syntax errors, you may have to go to the Command Palette while a `.js` file is open, and choose `Typescript: Select TypeScript Version...` to select the correct `+tildot` version of the TypeScript SDK.  If the TypeScript version is not displayed, carefully follow the above instructions again.

# TypeScript

[![Build Status](https://travis-ci.org/microsoft/TypeScript.svg?branch=master)](https://travis-ci.org/microsoft/TypeScript)
[![VSTS Build Status](https://dev.azure.com/typescript/TypeScript/_apis/build/status/Typescript/node10)](https://dev.azure.com/typescript/TypeScript/_build/latest?definitionId=4&view=logs)
[![npm version](https://badge.fury.io/js/typescript.svg)](https://www.npmjs.com/package/typescript)
[![Downloads](https://img.shields.io/npm/dm/typescript.svg)](https://www.npmjs.com/package/typescript)

[TypeScript](https://www.typescriptlang.org/) is a language for application-scale JavaScript. TypeScript adds optional types to JavaScript that support tools for large-scale JavaScript applications for any browser, for any host, on any OS. TypeScript compiles to readable, standards-based JavaScript. Try it out at the [playground](https://www.typescriptlang.org/play/), and stay up to date via [our blog](https://blogs.msdn.microsoft.com/typescript) and [Twitter account](https://twitter.com/typescript).

Find others who are using TypeScript at [our community page](https://www.typescriptlang.org/community/).

## Installing

For the latest stable version:

```bash
npm install -g typescript
```

For our nightly builds:

```bash
npm install -g typescript@next
```

## Contribute

There are many ways to [contribute](https://github.com/microsoft/TypeScript/blob/master/CONTRIBUTING.md) to TypeScript.
* [Submit bugs](https://github.com/microsoft/TypeScript/issues) and help us verify fixes as they are checked in.
* Review the [source code changes](https://github.com/microsoft/TypeScript/pulls).
* Engage with other TypeScript users and developers on [StackOverflow](https://stackoverflow.com/questions/tagged/typescript).
* Help each other in the [TypeScript Community Discord](https://discord.gg/typescript).
* Join the [#typescript](https://twitter.com/search?q=%23TypeScript) discussion on Twitter.
* [Contribute bug fixes](https://github.com/microsoft/TypeScript/blob/master/CONTRIBUTING.md).
* Read the language specification ([docx](https://github.com/microsoft/TypeScript/blob/master/doc/TypeScript%20Language%20Specification.docx?raw=true),
 [pdf](https://github.com/microsoft/TypeScript/blob/master/doc/TypeScript%20Language%20Specification.pdf?raw=true), [md](https://github.com/microsoft/TypeScript/blob/master/doc/spec.md)).

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see
the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com)
with any additional questions or comments.

## Documentation

*  [TypeScript in 5 minutes](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)
*  [Programming handbook](https://www.typescriptlang.org/docs/handbook/basic-types.html)
*  [Language specification](https://github.com/microsoft/TypeScript/blob/master/doc/spec.md)
*  [Homepage](https://www.typescriptlang.org/)

## Building

In order to build the TypeScript compiler, ensure that you have [Git](https://git-scm.com/downloads) and [Node.js](https://nodejs.org/) installed.

Clone a copy of the repo:

```bash
git clone https://github.com/microsoft/TypeScript.git
```

Change to the TypeScript directory:

```bash
cd TypeScript
```

Install [Gulp](https://gulpjs.com/) tools and dev dependencies:

```bash
npm install -g gulp
npm install
```

Use one of the following to build and test:

```
gulp local             # Build the compiler into built/local.
gulp clean             # Delete the built compiler.
gulp LKG               # Replace the last known good with the built one.
                       # Bootstrapping step to be executed when the built compiler reaches a stable state.
gulp tests             # Build the test infrastructure using the built compiler.
gulp runtests          # Run tests using the built compiler and test infrastructure.
                       # Some low-value tests are skipped when not on a CI machine - you can use the
                       # --skipPercent=0 command to override this behavior and run all tests locally.
                       # You can override the specific suite runner used or specify a test for this command.
                       # Use --tests=<testPath> for a specific test and/or --runner=<runnerName> for a specific suite.
                       # Valid runners include conformance, compiler, fourslash, project, user, and docker
                       # The user and docker runners are extended test suite runners - the user runner
                       # works on disk in the tests/cases/user directory, while the docker runner works in containers.
                       # You'll need to have the docker executable in your system path for the docker runner to work.
gulp runtests-parallel # Like runtests, but split across multiple threads. Uses a number of threads equal to the system
                       # core count by default. Use --workers=<number> to adjust this.
gulp baseline-accept   # This replaces the baseline test results with the results obtained from gulp runtests.
gulp lint              # Runs eslint on the TypeScript source.
gulp help              # List the above commands.
```


## Usage

```bash
node built/local/tsc.js hello.ts
```


## Roadmap

For details on our planned features and future direction please refer to our [roadmap](https://github.com/microsoft/TypeScript/wiki/Roadmap).
