Heroku Buildpack for Midgard MVC
================================

This is a [Heroku Buildpack](https://devcenter.heroku.com/articles/buildpacks) for running [Midgard MVC](http://midgard-project.org/midgardmvc/) applications.

## Setup

You need a Composer-installable Midgard MVC application, for example one built with the [Midgard MVC project template](https://github.com/midgardproject/midgardmvc-project-template). You also need a valid Heroku account and a working installation of the [Heroku toolbelt](https://toolbelt.heroku.com/).

### Buildpack setup

Add a `.buildpacks` file in the root of your application, with the following contents:

    https://github.com/piotras/heroku-buildpack-gettext
    https://github.com/piotras/heroku-buildpack-libgda-4
    https://github.com/piotras/heroku-buildpack-midgard2
    https://github.com/piotras/heroku-buildpack-pcre
    https://github.com/piotras/heroku-buildpack-lighttpd
    https://github.com/piotras/heroku-buildpack-php
    https://github.com/piotras/heroku-buildpack-php5-midgard2
    https://github.com/bergie/heroku-buildpack-midgard-mvc

This will tell which buildpacks Heroku needs to run when deploying your app. Since this means using multiple buildpacks, the actual setup will be run with the [multi-buildpack](https://github.com/ddollar/heroku-buildpack-multi) module.

### Heroku app setup

Create your application:

    $ heroku apps:create myapp

Define the correct buildpack:

    $ heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git

Deploy:

    $ git push heroku master
