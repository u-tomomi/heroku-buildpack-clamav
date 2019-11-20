heroku-buildpack-clamav
========================

A [heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for setting up a clamd daemon.

## Usage
    Add https://github.com/heroku/heroku-buildpack-apt to your buildpacks, before this buildpack
    Create a Aptfile with minimally, clamav-daemon and clamav-freshclam
    Add clamav-unofficial-sig if you'd like those signatures included
    Create a worker that starts clamd
