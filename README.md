# Table of Contents

* [Problem](#problem)
* [Solution](#solution)
* [Workflow](#workflow)
  * [Github](#github)
  * [Scrum and Agile Development](#scrum-and-agile-development)
  * [Taiga.io](#taiga)
  * [Slack](#slack)
  * [Testing](#testing)
* [Cloud Engine](#cloud-engine)
  * [Meteor](#meteor)
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

- ```master``` - should always be production-ready and error-free for new contributors to clone.
- ```testing``` - unit testing happens here.
- ```dev``` - completed features merged here
  + ```component_one``` - example: search bar
  + ```component_two```
  + ```etc```

To build a car, we need to identify the components that go into a car. Likewise, a personnel tracker has various [Components](#components). Contributors can clone the repo, ```git checkout``` a component branch, and start committing code. Trusted collaborators invited to the repo have full commit/push permissions. Others should submit a pull request.

Once a component is completed, we will merge it to ```dev``` and ensure that nothing breaks. After fixing the issues, we will merge the dev branch into ```testing``` branch. See the [Testing](#testing) section for more information. Finally, we merge into ```master```.

### Scrum and Agile Development

Modern software development is a relatively low-risk, low cost-of-failure process. We can build, break, and implement very quickly. Contrast this to engineering projects, where meticulous planning coordination is indispensable. Constructing a bridge through trial-and-error is too expensive. 

The Scrum methodology is an agile development framework that seeks to minimize friction between product owners and developers. Projects break down into "sprints", work sessions that last for a few weeks. The end of each sprint should result in a potentially shippable product or feature (ex: registration form). Each sprint contains a set of **user stories**, TODO list items of *what* we need to do. Each user story has a set of **tasks** that describe _how_ to do it. 

At the end of each sprint developers meet with the product owner(s) to present what has been accomplished, challenges encountered, and the goal for next sprint. The product owner provides project direction and additional guidance on the product. The goal is to **_maximize feedback loops_** to keep the product owners and developers in sync. 

[Rugby Scrum](https://www.youtube.com/watch?v=jUz1ytcnn3c)

### Taiga

Taiga is a Scrum management framework that allows us to create sprints and user stories. We can open/close tasks, assign them to members, document the amount of effort taken in points (since humans aren't good at estimating time). The Taiga backlog and sprint taskboards will be the primary way for members to see what needs to get done.

Visit: <https://tree.taiga.io/project/foodstamp-personneltracker/backlog>

### Slack

Slack allows us to communicate in a IRC/email fashion among members. You can share images, code snippets, emojis, and memes. Our Slack is webhooked to ```#taiga```, receiving user story or task updates pushed by Taiga.

Visit: <https://personneltracker.slack.com>

You can also download their app for mobile.
 
### ~~Heroku~~ Cloud Environment

~~Heroku is our cloud Platform-as-a-Service (Paas). If Github hosts the master source code, Heroku hosts the master product (personnel tracker web app). Learn more at <https://devcenter.heroku.com>~~~


Contributors will still be responsible for setting up their local environment however, as we will create different branches during different phases of development.  Outlined below are the different technologies, settings, and configurations necessary in order to get your local environment up and running. 


Documentation:  <https://docs.djangoproject.com/en/1.10/>

#### AngularJS

#### Node.js

#### MongoDB

Documentation:  <https://docs.mongodb.com>

## Components

#### Authentication portal

* Picture:  Unit logo
* Text field:  Username
* Text field:  Password 
* Button:  Sign in
* Link:  Forgot Password?
* Button:  Register

#### Registration page

* Text field:  First name
* Text field:  Last name
* Text field:  DOD number
* Text field:  Phone number
* Text field:  Home address
* Text field:  Organization
* Text field:  Rank

#### Notifications

* Left side pane
    - Button:  Add personnel request
    - Button:  Delete personnel request
    - Button:  Modify data request
    - Button:  Grant permissions request
    - Link:  Show archived
* Main view
    - Admin data
    - Etc

#### Dashboard

* Left side pane
    - Search field
    - Area to return list of names
* Center view

* Right pane
    - Button:  Edit data
    - Button:  Print report
    - Button:  Search
    - Button:  Statistics
    - Button:  Notifications
    - Button:  Settings
    - Button:  Logout

#### Roles and permissions

* Roles
    - S1
    - User
    - Admin
    - Leadership
* Permissions
    - Read
    - Write
    - Execute

#### Summary statistics

* MOS time in service
* Etc

## Use cases

#### Export/import CSV file format
#### Help/FAQ section
#### Users can update their data, but changes require approval from S1 before writing to storage (notifications)
#### Users can upload certificates to their profile
#### Individual-stat tracking (for appointments, sick, leave) 

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
