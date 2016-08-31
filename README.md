# Table of Contents

* [Problem](#problem)
* [Solution](#solution)
* [Workflow](#workflow)
* [Github](#github)
* [Scrum and Agile Development](#scrum-and-agile-development)
* [Taiga.io](#taiga.io)
* [Slack](#slack)
* [Heroku](#heroku)
  * [Virtualenv](#virtualenv)
  * [Django](#django)
  * [Nginx](#nginx)
  * [AngularJS](#angularjs)
  * [Node.js](#node.js)
  * [MongoDB](#mongodb)
* [Mockups](#mockups)

## Problem


Admin staff and HR sections upper, mid, and lower levels manage personnel data using numerous Excel spreadsheets and paper documents. This creates several challenges:

  * Unncessary duplication of personnel data
  * Inefficient information management flows
  * Leaders cannot quickly obtain reports and mine statistics

> Creating a central database with a web front-end will allow HR to easily search for information and compile reports.

## Solution


A Django web app with MongoDB database that allows administrative staff to:
* Register incoming personnel
* Search for individuals by name
* Add/modify/remove data as necessary for individuals
* Aggregate PDF certificates and documents

## Workflow


### Github

### Scrum and Agile Development

### Taiga.io

### Slack

The main communication system for team members.  Link to web app:

<https://personneltracker.slack.com/messages>

You can also download their app for mobile.
 
### Heroku

Heroku is our cloud Platform-as-a-Service (Paas) of choice.  It will allow the team to build, deliver, monitor and scale our personnel tracker during development.  Learn more about Heroku at <https://devcenter.heroku.com>  

So here's the deal, Heroku will be connected to our source code hosted at <https://github.com/foodstamp/personneltracker>, and as the master branch accepts pull requests the main prototype will be updated with the new code.  

Contributors will still be responsible for setting up their local environment however, as we will create different branches during different phases of development.  Outlined below are the different technologies, settings, and configurations necessary in order to get your local environment up and running. 

* Before starting, the following need to be installed locally
  - Python 2.7
  - Pip
  - Virtualenv
     + ``` pip install virtualenv  ```
  - Postgres 
     + [Postgres](https://devcenter.heroku.com/articles/heroku-postgresql#local-setup)

#### Virtualenv

Refer to this link for setting up your Python virtual environment:

<https://docs.python-guide.org/en/latest/dev/virtualenvs/>

#### Django

Documentation:  <https://docs.djangoproject.com/en/1.10/>

#### Nginx

#### AngularJS

#### Node.js

#### MongoDB

Documentation:  <https://docs.mongodb.com>

## Mockups

Visual representation of requirements

#### Login
![Login](https://github.com/huckfynn/personnelTracker/blob/master/wireframes/login.png)

#### Registration

![Registration](https://github.com/huckfynn/personnelTracker/blob/master/wireframes/registration.png)

#### Dashboard

![Dashboard](https://github.com/huckfynn/personnelTracker/blob/master/wireframes/dashboard.png)

#### Viewing Notifications

![Notifications](https://github.com/huckfynn/personnelTracker/blob/master/wireframes/notifications.png)

#### Setting Roles and Persmissions

#### Organization Summary Statistics
