# heroku-integrated-firefox-geckodriver

[![Build Status](https://travis-ci.org/pyronlaboratory/heroku-integrated-firefox-geckodriver.svg?branch=master)](https://travis-ci.org/pyronlaboratory/heroku-integrated-firefox-geckodriver)
[![Requirements Status](https://requires.io/github/pyronlaboratory/heroku-integrated-firefox-geckodriver/requirements.svg?branch=master)](https://requires.io/github/pyronlaboratory/heroku-integrated-firefox-geckodriver/requirements/?branch=master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> Available for download at [The Heroku Elements Marketplace](https://elements.heroku.com/). Search `heroku-integrated-firefox-geckodriver` on the official Heroku Elements Marketplace to access the buildpack.


Buildpack `heroku-integrated-firefox-geckodriver` enables your application or client code - running in any high-level language such as *Python, Ruby or Node.js* - to access **Firefox** along with **Geckodriver** (the Selenium driver for Firefox) in a Heroku slug and enables the driver objects to perform automated operations defined in the source code.

Installation:
-----

To install and integrate the buildpack with your application running on Heroku's dyno:

```shell
$ heroku create --buildpack https://github.com/pyronlaboratory/heroku-integrated-firefox-geckodriver

# or if your app is already created:
$ heroku buildpacks:add https://github.com/pyronlaboratory/heroku-integrated-firefox-geckodriver

$ git push heroku master
```
Configurations:
---------------
Update Heroku's environment variables to store the following path strings. 
                                
  
**FIREFOX_BIN**: */app/vendor/firefox/firefox*

**GECKODRIVER_PATH**: */app/vendor/geckodriver/geckodriver*

**LD_LIBRARY_PATH**: */usr/local/lib:/usr/lib:/lib:/app/vendor*

**PATH**: */usr/local/bin:/usr/bin:/bin:/app/vendor/*

                

These configuration vars can be updated via Heroku CLI as follows:

Executable command: `heroku config:set <ENV_VARIABLE>=<ABSOLUTE_PATH>`

```shell

$ heroku config:set FIREFOX_BIN=/app/vendor/firefox/firefox

Setting FIREFOX_BIN and restarting python-app... done, v6
FIREFOX_BIN: '/app/vendor/firefox/firefox'

```


Go ahead and scrape the universe. Drop a star if you like this small project!
