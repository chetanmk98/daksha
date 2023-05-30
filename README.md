Daksha
===============================================

## Introduction
Daksha is a django framework based dynamic test case execution API.You can write any variation of UI-based test cases in a yml file and execute them right away with this new tool in town. <br /> For example: Sign in to any of your social media account and sign out or sign in then perform a task and then sign out. <br /> The API request should comprise of the location of the yml file.To summarize in simple terms the working can be divided into two steps -
* [Sending API Request](daksha_know-how/ApiRequest.md)
* [Writing Test Case](daksha_know-how/CreateTest.md)

You can also auto-generate test yamls through Daksha Recorder [chrome extension](ChromeExtension/Readme.md).
## Building and Running

### Using docker

  - Setup a local or remote chromedriver for your tests
  - Take a look at [docker-compose.yml](docker-compose.yml) file and create all the necessary [environment variables](#environment-variables).
  - Run the command `docker-compose up -d` to initiate the build and deploy the project.
  
  - NOTE: If you're running the application through docker and intend to run scripts saved locally, make sure to mount the location of test yamls to the container so that test yamls could be accessed from inside of container.

### Local deployment (without docker)

  - Download [python 3.8+](https://www.python.org/downloads/) and setup a [virtual environment](https://docs.python.org/3/tutorial/venv.html)
  - Install all requirements using `pip install -r requirements.txt`
  - (Optional) Create any env variables needed.
  - Download Chromedriver (https://chromedriver.chromium.org/downloads)
  - Run `python manage.py runserver` to start the project

## Setting up webdriver
We only support chromedriver at this point.

### Local Webdriver
Download Chromedriver according to your chrome version from https://chromedriver.chromium.org/downloads. You can later refer this path from your test yml.

### Remote Webdriver
Setup selenium grid using https://www.selenium.dev/downloads/. Or if you want to use the dockerized version you can download and run selenium grid images from dockerhub: https://hub.docker.com/u/selenium.

## #Environment Variables
You can configure the application in a lot of ways by setting the following environment variables:
* **STORAGE_PATH**
  * This is the location of directory where reports generated by the application are stored.
  * Defaults to 'reports' in current directory.

* **APACHE_URL**
  * If you're using a hosting service (like apache) to host your reports, put the base URL here.
  * Make sure that this base url is mapped to whatever location the reports are stored. (governed by **STORAGE_PATH** environment variable)

* **LOG_FILE**
  * This is the location where reports generated by the application are stored.
  * Defaults to 'logs/uiengine.log' in current directory.

* **POSTMARK_TOKEN**
  * This is the postmark token which will be used to send reports by email.
  * If not set, we'll skip sending the email.
  
* **ALERT_URL**
  * This is the alert webhook url which will be used to send alerts in gchat/slack.
  * If not set, we'll skip sending the alert.
  
* **EMAIL_HOST_USER**
  * This is the email ID from which reports should be sent.

* **GIT_USER**
  * Github username for logging into github to fetch test yamls.
  * Don't set it/Leave it blank if the repo is public and no authentication is needed.

* **GIT_PASS**
  * Github password for logging into github to fetch test yamls.
  * Don't set it/Leave it blank if the repo is public and no authentication is needed.

* **REPO_USER**
  * Name of user who owns the github repository containing the test yamls.
  * Only one of the variables **REPO_USER** and **REPO_ORG** should be set at a time.

* **REPO_ORG**
  * Name of organization which owns the github repository containing the test yamls.
  * Only one of the variables **REPO_USER** and **REPO_ORG** should be set at a time.

* **REPO_NAME**
  * Name of the github repository containing the test yamls.

* **BRANCH_NAME**
  * Name of the branch containing the test yamls in the github repository defined by **REPO_NAME**.

* **DJANGO_SECRET_KEY**
  * Use this variable if you want to override the default value of SECRET_KEY for added security.

* **ALLOWED_HOSTS**
  * Provide a comma separated list of hosts which you'd like to be added to ALLOWED_HOSTS.

## Get in Touch

* Open an issue at: https://github.com/mykaarma/daksha/issues
* Email us at: opensource@mykaarma.com

## Contributions

We welcome contributions to Daksha. Please see our [contribution guide](CONTRIBUTING.md) for more details.

## License
Copyright 2021 myKaarma

Licensed under the [GNU Affero General Public License v3](LICENSE)

## Motivation

[Information Modal](https://github.com/mykaarma/information-modal)
