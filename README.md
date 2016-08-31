# Table of Contents

* [Problem](#problem)
* [Solution](#solution)
* [Workflow](#workflow)
* [Github](#github)
* [Scrum and Agile Development](#scrum-and-agile-development)
* [Taiga.io](#taiga)
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

We need a suite of development tools and techniques to synchronize our development efforts. Below are the various components:

### Git

Google Docs provides synchronous, real-time collaboration. Git is asynchronous, allowing people to do things offline. Github hosts our repository (master copy of the code). To download a copy from the repository:
```sh
git clone https://github.com/foodstamp/personneltracker.git
```
Set up the username/email paramaters for git config:
```sh
git config --global user.name "<username>"
git config --global user.email "<email address>"
```
If you are using HTTPS instaed of SSH, you will have to authenticate with username and password every push. Caching your credentials for one hour will make life easier:
```sh
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=3600'
```
Before starting work and before submitting anything you should *always* synchronize with the repo:
```sh
git fetch
git merge
```
To send files upstream, use:
```sh
git add <file/folder>
git commit -m "<message>"
git push -u origin master
```

Add will queue up the files you've added. Commit records a message for what you've done and preps the files to go upstream. Push syncs your local copy of the branch to the master copy on the repo.

Sometimes as you are working, someone else will have already pushed to the master. When you do a ``` git fetch ``` and ``` git merge ``` to sync with the master, this will wipe out your progress. Save your work using:

```sh
git stash
```

Complete the synchronization, then to restore your work:

```sh
git stash apply
```

Some other git commands to use and study:

```sh
git checkout
git log
git status
```

<https://git-scm.com/docs/gittutorial> is a great resource to learn Git.

#### Branches

The ``` master ``` branch should always be production-ready and error-free for new contributors to clone. Development of new code will happen on the ``` dev ``` branch. Trusted collaborators invited to the repository have full commit/push permissions. Others should fork the branch onto their local machines, do work, then submit a pull request. We will add new branches to the Github repository as neccessary.


### Scrum and Agile Development

### Taiga

### Slack

The main communication system for team members. Visit: <https://personneltracker.slack.com>

You can also download their app for mobile.
 
### Heroku

Heroku is our cloud Platform-as-a-Service (Paas). If Github hosts the master source code, Heroku hosts the master product (personnel tracker web app). Learn more at <https://devcenter.heroku.com>  

Heroku will be connected to our source code hosted at <https://github.com/foodstamp/personneltracker>, and as the master branch accepts pull requests the main prototype will be updated with the new code.  

Contributors will still be responsible for setting up their local environment however, as we will create different branches during different phases of development.  Outlined below are the different technologies, settings, and configurations necessary in order to get your local environment up and running. 

* Before starting, the following need to be installed locally
  - Python 2.7
  - Pip
  - Virtualenv
    + ``` pip install virtualenv  ```
  - MongoDB
     + [Django MongoDB Engine](https://django-mongodb-engine.readthedocs.io/en/latest/)
  - Django

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
