
# heroku-integrated-firefox-geckodriver

[![Build Status](https://travis-ci.org/pyronlaboratory/heroku-integrated-firefox-geckodriver.svg?branch=master)](https://travis-ci.org/pyronlaboratory/heroku-integrated-firefox-geckodriver)
[![Requirements Status](https://requires.io/github/pyronlaboratory/heroku-integrated-firefox-geckodriver/requirements.svg?branch=master)](https://requires.io/github/pyronlaboratory/heroku-integrated-firefox-geckodriver/requirements/?branch=master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> Now supports Heroku-20, and legacy versions Heroku-16 and Heroku-18.

> Available for download at [The Heroku Elements Marketplace](https://elements.heroku.com/). Search `heroku-integrated-firefox-geckodriver` on the official Heroku Elements Marketplace to access the buildpack.


Buildpack `heroku-integrated-firefox-geckodriver` enables your application or client code - running in any high-level language such as Python, Ruby or Node.js - to access Firefox along with Geckodriver (the Selenium driver for Firefox) in a Heroku slug and enables the driver objects to perform automated operations defined in the source code.

Version compatibility as follows:

- Firefox v82.0.3
- Geckodriver v0.28.0


# Installation:


To install and integrate the buildpack with your application running on Heroku's dyno:

```shell
$ heroku create --buildpack https://github.com/pyronlaboratory/heroku-integrated-firefox-geckodriver

# or if your app is already created:
$ heroku buildpacks:add https://github.com/pyronlaboratory/heroku-integrated-firefox-geckodriver

$ git push heroku master
```

# Configurations:

Update Heroku's environment variables to store the following path strings. 
                                
  
**FIREFOX_BIN**: */app/vendor/firefox/firefox*

> Alternatively, you can even use */app/vendor/firefox/firefox-bin*

**GECKODRIVER_PATH**: */app/vendor/geckodriver/geckodriver*

**LD_LIBRARY_PATH**: */usr/local/lib:/usr/lib:/lib:/app/vendor*

**PATH**: */usr/local/bin:/usr/bin:/bin:/app/vendor/*

                

These configuration variables can be updated via Heroku CLI as follows:

Executable command: `heroku config:set <ENV_VARIABLE>=<ABSOLUTE_PATH>`

```shell

$ heroku config:set FIREFOX_BIN=/app/vendor/firefox/firefox

Setting FIREFOX_BIN and restarting python-app... done, v6
FIREFOX_BIN: '/app/vendor/firefox/firefox'

```
# Implementation:

## Python

#### app.py
```
import os
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.firefox.firefox_binary import FirefoxBinary

def  load_driver():
	options = webdriver.FirefoxOptions()
	
	# enable trace level for debugging 
	options.log.level = "trace"

	options.add_argument("-remote-debugging-port=9224")
	options.add_argument("-headless")
	options.add_argument("-disable-gpu")
	options.add_argument("-no-sandbox")

	binary = FirefoxBinary(os.environ.get('FIREFOX_BIN'))

	firefox_driver = webdriver.Firefox(
		firefox_binary=binary,
		executable_path=os.environ.get('GECKODRIVER_PATH'),
		options=options)

	return firefox_driver

def  start():
	driver = load_driver()
	driver.get("https://www.google.com/")
	print(driver.title)
	driver.close()

if  __name__ == "__main__":
	start()
```
**NOTE:** Make sure to add a ***requirements.txt*** file with relevant packages, and add the following entry to your ***Procfile***:
 
`worker: python app.py`


## Ruby

#### app.rb
```
require  'selenium-webdriver'

options = Selenium::WebDriver::Firefox::Options.new

options.add_argument('--remote-debugging-port=9222')
options.add_argument('--headless')
options.add_argument('--disable-gpu')
options.add_argument('--no-sandbox')

Selenium::WebDriver::Firefox::Binary.path=ENV['FIREFOX_BIN']
Selenium::WebDriver::Firefox::Service.driver_path=ENV['GECKODRIVER_PATH']
  
# use argument `:debug` instead of `:info` for detailed logs in case of an error
Selenium::WebDriver.logger.level = :info 

driver = Selenium::WebDriver.for :firefox, options: options
driver.get "https://www.google.com"
puts  "#{driver.title}"
driver.quit
```
A minimalist ***Gemfile*** 
```
source "https://rubygems.org"
gem 'selenium-webdriver', '3.142.7'
```
and ***Gemfile.lock*** file
```
GEM
  remote: https://rubygems.org/
  specs:
    childprocess (3.0.0)
    rubyzip (2.3.0)
    selenium-webdriver (3.142.7)
      childprocess (>= 0.5, < 4.0)
      rubyzip (>= 1.2.2)

PLATFORMS
  x64-mingw32

DEPENDENCIES
  selenium-webdriver (= 3.142.7)

BUNDLED WITH
   2.2.19

```
**NOTE:** Run `heroku run bash` from your local machine to test your script. Execute command  `ruby app.rb` via bash to see result.

## Node.js

#### app.js
```
const { Builder } = require('selenium-webdriver');
const { Options, firefox } = require('selenium-webdriver/firefox');

const  options = new  Options()
 .headless()
 .setBinary(`${process.env.FIREFOX_BIN}`);

(async  function  example() {
	let  driver = new  Builder()
	 .forBrowser('firefox')
	 .setFirefoxOptions(options)
	 .build();

	try {
		await  driver.get('https://www.google.com/');
		console.log(await  driver.getTitle());
	}
	catch(err) {
		console.log(err.message);
	}
	finally {
		await  driver.quit();
	}
})();
```
**NOTE:** Make sure to add a ***package.json*** file with relevant packages, and add the following entry to your ***Procfile***:
 
`worker: node app.js`


Go ahead and scrape the universe. Drop a star if you like this small project!

<a href="https://ko-fi.com/F1F1VEXA" target="_blank"><img src="ko-fi.png" alt="Buy me a Ko-fi, will ya?!" width="200"/></a>
