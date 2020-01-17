# heroku-integrated-firefox-geckodriver

[![Build Status](https://travis-ci.org/pyronlaboratory/heroku-integrated-firefox-geckodriver.svg?branch=master)](https://travis-ci.org/pyronlaboratory/heroku-integrated-firefox-geckodriver)
[![Requirements Status](https://requires.io/github/ronnielivingsince1994/heroku-integrated-firefox-geckodriver/requirements.svg?branch=master)](https://requires.io/github/ronnielivingsince1994/heroku-integrated-firefox-geckodriver/requirements/?branch=master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This buildpack installs Firefox alongwith mozilla/geckodriver (the Selenium driver for Firefox) in a Heroku slug.

Usage:
-----

Example usage:

```shell
$ heroku create --buildpack https://github.com/ronnielivingsince1994/heroku-integrated-firefox-geckodriver

# or if your app is already created:
$ heroku buildpacks:add https://github.com/ronnielivingsince1994/heroku-integrated-firefox-geckodriver

$ git push heroku master
```
Configurations:
---------------
Updating config vars on Heroku CLI:

```
FIREFOX_BIN:      /app/vendor/firefox/firefox

GECKODRIVER_PATH: /app/vendor/geckodriver/geckodriver

LD_LIBRARY_PATH:  /usr/local/lib:/usr/lib:/lib:/app/vendor

PATH:             /usr/local/bin:/usr/bin:/bin:/app/vendor/

```

Go ahead and scrape the universe. Drop a star if you like this small project!
