# heroku-buildpack-clamav

## What is this?

It is a [heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for setting up a clamd daemon.

## Usage

1. Login to your Heroku app dashboard and click on `Settings`.  Then scroll to `Buildpacks`.
2. At the bottom of the buildpack order, add the following two buildpacks, in the following order:
    + `https://github.com/heroku/heroku-buildpack-apt` (a buildpack offered by Heroku that adds support for apt-based dependencies)
    + `https://github.com/bradleymarques/heroku-buildpack-clamav` (this buildpack).
3. Open your rails project.
4. In the root directory, add a new file named `Aptfile` (without extension)
5. Add the following content to this file:

```
# Aptfile
# Install required apt packages

clamav-daemon
clamav-freshclam
```

6. (UNSURE) Create a worker that starts clamd
