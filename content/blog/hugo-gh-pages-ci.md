+++
date = "May 13, 2018"
title = "Hugo on GitHub Pages using Travis-CI for deployment"
math = "false"
draft = "false"
+++

# Hugo on GitHub Pages using Travis-CI for deployment

This post shows how to automate building and deployment of [Hugo](https://gohugo.io/) static websites to GitHub Pages using [Travis CI](https://travis-ci.org/). Builds are automatically triggered when pushing to the Git repository on the master branch, and deployment when a build on the master branch succeeds.

Hugo is a static website generator written in Go, and only requires a single binary. The easiest way to run Hugo in the Travis CI container is by including the specific hugo binary with which to build the site as part of the repository (eg. in the directory `/binaries`). This way you don’t need to download the Hugo release on each build job, which may take several minutes. You can get the latest binary from the [Hugo releases page](https://github.com/spf13/hugo/releases) (use the `hugo_<VERSION>_Linux-64bit.tar.gz` file and include only the `hugo` binary).

For syntax highlighting, you also need [Pygments](http://pygments.org/) installed. In the `.travis.yml` file this is done by specifying the `python-pygments` package as [apt addon](https://docs.travis-ci.com/user/installing-dependencies/#Installing-Packages-with-the-APT-Addon).

### Configuring Travis CI

On the Travis CI homepage on your [profile page](https://travis-ci.org/profile) you need to enable the GitHub repository you want to build.

Travis CI also needs write-access to the GitHub repository, to be able to update the `gh-pages` branch. For this we provide a GitHub token environment variable named `GITHUB_TOKEN` in this example. Environment variables can be specified on the Travis CI website in the repository settings (see the [Travis environment variables docs](https://docs.travis-ci.com/user/environment-variables/#Defining-Variables-in-Repository-Settings)). You can generate this token in your GitHub account settings under “[Personal access tokens -> Generate new token](https://github.com/settings/tokens/new)” (ensure that the “repo” checkbox is enabled).



```yaml
# Install the apt prerequisites
addons:
  apt:
    packages:
      - python-pygments

# Clean and don't fail
install:
  - rm -rf public || exit 0

# Build the website
script:
  - ./binaries/hugo # --theme=ghoust

# Deploy to GitHub pages
deploy:
  provider: pages
  skip_cleanup: true
  local_dir: public
  github_token: $GITHUB_TOKEN # Set in travis-ci.org dashboard
  on:
    branch: master
```