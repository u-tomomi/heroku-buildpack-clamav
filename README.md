# heroku-buildpack-clamav

## What is this?

It is a [heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for setting up a [Clam Antivirus](https://www.clamav.net/) daemon.

## Usage

1. Login to your Heroku app dashboard and click on `Settings`.  Then scroll to `Buildpacks`.
2. At the top of the buildpack list, add the following two buildpacks, in the following order:
    + `https://github.com/heroku/heroku-buildpack-apt` (a buildpack offered by Heroku that adds support for apt-based dependencies)
    + `https://github.com/bradleymarques/heroku-buildpack-clamav` (this buildpack).
3. Open your rails project.
4. In the root directory, add a new file named `Aptfile` (without extension)
5. Add the following content to this file:

```sh
# Aptfile
# This file lists the required apt packages.  These are installed by the heroku-buildpack-apt buildpack
# See https://github.com/heroku/heroku-buildpack-apt for details

# Antivirus
clamav
clamav-daemon
clamav-freshclam
```

6. Add the following file to your Rails project: `config/antivirus/freshclam.conf`.
7. Add the following contents to this file:

```sh
# config/antivirus/freshclam.conf
# This config file specifies where the application 'freshclam' looks for virus definition databases

DatabaseMirror database.clamav.net
```

8. Also add the following file to your Rails project: `config/antivirus/clamd.conf`.
9. Add the following contents to this file:

```sh
# config/antivirus/clamd.conf

# TODO: I AM NOT SURE WHAT NEEDS TO BE IN THIS FILE
```

10. (UNSURE) Create a worker that starts clamd
