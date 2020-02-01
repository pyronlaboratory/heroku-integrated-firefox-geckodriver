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
-----

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

[![ko-fi](https://ucc51d32fd46bfbb4d3f4c7a9a3a.previews.dropboxusercontent.com/p/pdf_img/AAsPd8cjapw5AOvrc8C9RWabxLHG9K0FZCAFdyFbtg8ZRtlcjN-TwykKdo6a3YAyXKuSNjXhTv3VJhoACO-WcZw8gEeWBOsrBxTVVLdfEVEon09bsYCmmHRZL_6GJuFxiF0_Zh8O3xpx1b7AOqD2pb1APSvPwDW6cL1xdgq54Xt3bcKkxvE7u2N9fmPYp_lE3NizblboiO6l6CfcsuxgvFTlTFaw-9Xh0j2AH4qeBuv2YAc9frjEFMDKa8McObiboj9NqX7MpKsNNGQZnzfzqC9MtNXtQMHlB3V17nnAIvpeQefLvOapEwPiRM-cSJ3QWr6E6SChtSX-V__yUVg_7MxyF-Kasi0sfjvNE3DBtrBJ29PVTbUzP2FwR_5PllJ9aRNKoet1E0pb5-cS0d78JGE_IP5alI8s8ojcQQjXjYvO_Q/p.png?page=0&scale_percent=15)](https://ko-fi.com/F1F1VEXA)
