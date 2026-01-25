# Dotfiles

There are several standard dotfiles that should be included in most projects.

## .gitignore

The convention for the .gitignore files is to use a generated template from the following site (example for Go application):

https://www.toptal.com/developers/gitignore/api/macos,eclipse,windows,intellij,visualstudiocode,go

This allows for a standard .gitignore file that covers common IDEs and operating systems, along with the specific language or framework being used.

In the case of applications that generate additional artifacts, either binary compiled files or generated static files, those paths should be added to the top of the .gitignore file between the top comment and the first section header.

## .dockerignore

Any project with a Dockerfile should include a minimal .dockerignore file to prevent unnecessary files from being included in the Docker build context. At a minimum this should focus on excluding version control directories and files.

## .clip4llm

The [clip4llm](https://github.com/UnitVectorY-Labs/clip4llm) is used with most projects in UnitVectorY-Labs and therefore it is useful to include the appropriate `.clip4llm` configuration file based on the project type.

For a minimal project ignoring the LICENSE file is recommended:

```
exclude=LICENSE
```

For projects that generate additional files, be that Java and its `target` folder or generated content that takes up a significant amount of space, and therefore context window of an LLM, should be excluded as well.

```
exclude=target,LICENSE
```

## .repver

The [repver](https://github.com/UnitVectorY-Labs/repver) project is configured for some applications, specifically including those that use Go.  This project provides a way to have a standardized file that allows for the scripting of updating files across multiple files.  This means that some files have conventions for comments including the go version in the `go.mod` file being suffixed with ` // GOVERSION`.

There are standard patterns used by the different types of repos for the common configuration that will update versions across multiple files including the `go.mod`, `Dockerfile`, and GitHub Actions files.

Additional version patterns for other libraries outside of Go are added.  This isn't meant to replace Dependabot though, this supplements it by updating version numbers in multiple places concurrently.
