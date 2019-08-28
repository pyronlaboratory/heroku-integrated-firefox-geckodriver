# heroku-integrated-firefox-geckodriver
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
<<<<<<< HEAD

GECKODRIVER_PATH: /app/vendor/geckodriver/geckodriver

LD_LIBRARY_PATH:  /usr/local/lib:/usr/lib:/lib:/app/vendor

=======
GECKODRIVER_PATH: /app/vendor/geckodriver/geckodriver
LD_LIBRARY_PATH:  /usr/local/lib:/usr/lib:/lib:/app/vendor
>>>>>>> a8ea6a25de2d69775d3601e99c2244975ed4e5fe
PATH:             /usr/local/bin:/usr/bin:/bin:/app/vendor/

```
