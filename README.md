# Table of Contents

* [Problem](#problem)
* [Solution](#solution)
* [Timeline](#timeline)
* [Workflow](#workflow)
  * [Github](#github)
    * [Branches](#branches)
  * [Scrum and Agile Development](#scrum-and-agile-development)
  * [Taiga.io](#taiga)
  * [Slack](#slack)
  * [Testing](#testing)
* [Cloud Engine](#cloud-engine)
  * [Meteor](#meteor)
  * [AngularJS](#angularjs)
  * [Node.js](#node.js)
  * [MongoDB](#mongodb)
* [Components](#components)
  * [Security](#security)
  * [Authentication Portal](#authentication-portal)
  * [Registration Page](#registration-page)
  * [Dashboard](#dashboard)
  * [Mockups](#mockups)

## Problem


Admin staff and HR sections upper, mid, and lower levels manage personnel data using numerous Excel spreadsheets and paper documents. This creates several challenges:

  * Unncessary duplication of personnel data
  * One person editing a spreadsheet locks it for others
  * Inefficient information management flows
  * Leaders cannot quickly obtain reports and mine statistics

> Creating a central database with a web front-end will allow HR to easily search for information and compile reports.

## Solution

A web app with MongoDB database that allows administrative staff to:
* Register incoming personnel
* Search for individuals by name
* Add/modify/remove data as necessary for individuals
* Aggregate PDF certificates and documents

> [See a mockup examples](#mockups)

## Timeline

This is likely to shorten or expand as we progress. Project breakdown:

* ~~_Planning: (1 week)_~~
  * ~~Identifying stakeholders, gathering requirements~~
  * ~~Drafting wireframes, product specifications~~
* _Environment Setup: (2 weeks)_
  * Installing/configuring virtual machines and software platforms
* _Phase I: (3 weeks)_
  * Front-end website
  * Individuals able to register and fill out forms; data stored in MongoDB
* _Phase II: (4 weeks)_
  * Web application
  * Individuals can view their profiles
  * HR can search through database
  * Can add/remove/modify information
* _Phase III: (2 weeks)_
  * Roles and Authentication
  * Grant access permissions based on roles and scope (Unit, Section, Division)
* _Phase IV: (2 weeks)_
  * Testing
  * Import Excel sheets as CSV into new database
  * Bug hunting and troubleshooting
* _Phase V: (2 weeks)_
  * Deployment
  * Migrate code and server, allow internal network access
  * Web app deployed in production 

## Workflow

We need a suite of development tools and techniques to synchronize our development efforts. Below are the various components:

### Github

Google Docs provides synchronous, real-time collaboration. Git is asynchronous, allowing people to do things offline. Github hosts our repository (master copy of the code). To download a copy from the repository:
```sh
git clone https://github.com/foodstamp/personneltracker.git
```
Set up the username/email paramaters for git config:
```sh
git config --global user.name "<username>"
git config --global user.email "<email address>"
```
If you are using HTTPS instead of SSH, you will have to authenticate with username and password every push. Caching your credentials for one hour will make life easier:
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

Add will queue up the files you've added and/or edited. Commit records a message for what you've done and preps the files to go upstream. Push syncs your local copy of the branch to the master copy on the repo.

Sometimes as you are working, someone else will have already pushed to the master. When you do a ``` git fetch ``` and ``` git merge ``` to sync with the master, this will wipe out your progress. Save your work using:

```sh
# Save your work
git stash

# Complete the synchronization, then to restore your work:
# git stash apply
```
Some other git commands to use and study:
  ```sh
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

```sh
# List all of the branches in the local repository:
git branch

# To create a new branch and then check it out: 
git branch <name>
git checkout <name>

# You can also just use:
git checkout -b <name>

# To delete a branch:
git branch -d <name>

# To rename the current branch to <name>:
git branch -m <name>

# To merge <branch> into the *current* branch:
git merge <branch>

# To push a local branch to remote
git push -u origin <branch>

# To delete a remote branch (dangerous!)
git push origin --delete <remote_branch>
```

##### Example

```sh
# Start a new feature
git checkout -b new-feature master

# Edit some files
git add <file>
git commit -m "Start a feature"

# Edit some files
git add <file>
git commit -m "Finish a feature"

# Merge in the new-feature branch
git checkout master
git merge new-feature
git branch -d new-feature
```

### Scrum and Agile Development

Modern software development is a relatively low-risk, low cost-of-failure process. We can build, break, and implement very quickly. Contrast this to engineering projects, where meticulous planning coordination is indispensable. Constructing a bridge through trial-and-error is too expensive. 

The Scrum methodology is an agile development framework that seeks to minimize friction between product owners and developers. Projects break down into "sprints", work sessions that last for a few weeks. The end of each sprint should result in a potentially shippable product or feature (ex: registration form). Each sprint contains a set of **user stories**, TODO list items of *what* we need to do. Each user story has a set of **tasks** that describe _how_ to do it. 

At the end of each sprint developers meet with the product owner(s) to present what has been accomplished, challenges encountered, and the goal for next sprint. The product owner provides project direction and additional guidance on the product. The goal is to **_maximize feedback loops_** to keep the product owners and developers in sync. 

[Rugby Scrum](https://www.youtube.com/watch?v=jUz1ytcnn3c)

### Taiga

Taiga is a Scrum management framework that allows us to create sprints and user stories. We can open/close tasks, assign them to members, document the amount of effort taken in points (since humans aren't good at estimating time). The Taiga backlog and sprint taskboards will be the primary way for members to see what needs to get done.

Visit: <https://tree.taiga.io/project/foodstamp-personneltracker/backlog>

### Slack

Slack allows us to communicate in an IRC/email fashion among members. You can share images, code snippets, emojis, and memes. Our Slack is webhooked to ```#taiga```, receiving user story or task updates pushed by Taiga.

Visit: <https://personneltracker.slack.com>

You can also download their app for mobile.
 
### Testing

Test-driven development focuses on very short software development cycles, continually tested against specific requirements and test cases. Software is only added if it can pass all the tests.This reduces the amount of time in unnecessary debugging and bug-hunting. The cycle goes:

1. Add a test to define a function or improvement
2. Run all the tests and see if this new one fails
3. Write the code to make the test pass
4. Run all the tests again
5. Refactor and clean code, removing duplication
6. Repeat

![TDD](https://upload.wikimedia.org/wikipedia/commons/0/0b/TDD_Global_Lifecycle.png)

Testing the entire web app will be a different, albeit similar process. [Please read the Meteor testing guide](https://guide.meteor.com/testing.html)

### Cloud Engine

Just as Github hosts the master source code, we need an engine to host the master product (personnel tracker web app) that allows collaborators to access and test. Heroku, Google Compute, Amazon EC2 are all prospective options.

Contributors will still be responsible for setting up their local environment, however, as we will be working on different branches. Below are the different technologies we will use in our development stack.

#### Meteor

[Meteor](https://www.meteor.com/) is a web framework written in [Node.js](https://nodejs.org/en/) (server-side javascript runtime environment). Using Meteor lets us quickly build a web app using a single programming language and integrates well with MongoDB. No need to glue different frameworks together. Download the installer and do the tutorial.

#### MongoDB

MongoDB is a NoSQL (non-relational) database, scaling well with large datasets (supports paralellism). It stores data in JSON, which is human-readable:

```javascript
{
    '_id' : 1,
    'name' : { 'first' : 'John', 'last' : 'Backus' },
    'contribs' : [ 'Fortran', 'ALGOL', 'Backus-Naur Form', 'FP' ],
    'awards' : [
        {
            'award' : 'W.W. McDowell Award',
            'year' : 1967,
            'by' : 'IEEE Computer Society'
        }, {
            'award' : 'Draper Prize',
            'year' : 1993,
            'by' : 'National Academy of Engineering'
        }
    ]
}
```

The key-value design lets us throw different data fields or even large objects like PDFs at the database. Opt-ing out of SQL will provides flexibility for the personnel tracker.

Documentation:  <https://docs.mongodb.com> 

#### AngularJS

AngularJS is for client-side web page interaction. Depending on how mature the Meteor front-end engine is, we may or may not use this.

More information: <https://angularjs.org/>

#### Bootstrap

Bootstrap makes the front-end webpage HTML/CSS nice. Templates, themes, glamor.

<https://getbootstrap.com/getting-started/#examples>

## Components

Refer to the [Mockups](#mockups) for a visual understanding of the project. 

> This section needs expansion. Feel free to contribute components and ideas.

### Security

* AES-256 for MongoDB
* HTTPS connection to website. [Let's Encrypt](https://letsencrypt.org/)

### Authentication Portal

This is the landing page for the personnel tracker.
* Prettified page with organization logo
* Users can login with email/password (creds somewhere securely)
* Users can recover forgotton password via email
* New users can navigate to registration page
* Smartcard authentication in the future

### Registration Page

Person in-processing the organization creates their account for the first time.
* Administrative data
* Login credentials
* Users receive confirmation email for their account
* NEED MORE ITEMS

### Dashboard

Primary view allows users to access database. 

* [Search functionality](#search-bar)
* [Personnel Profiles](#personnel-profiles)
* [Editing Data](#editing-data)
* [Navigation toolbar](#navigation)
* [Roles and Permissions](#roles-and-permissions)
* [Notifications](#notifications)
* [Status Reports](#status-reports)
* [Uploading Documents](#uploading-documents)
* [Export/Import CSV](#export/import-csv)
* [Help/FAQ](#help/faq)


#### Search Bar

Authorized users can search for individuals' names. Can also search by other fields (organization, status, etc).

#### Personnel Profiles

Displays an individual's information for the user based on the user's read/view permissions. User can download documents associated with personnel data.

#### Editing Data

Users can edit their data and upload substantiating documents. For example, changing one's last name would require a marriage certificate justifying the change. Changes submitted to staff for approval.

#### Navigation

A sidebar that allows users to access different web app functions (PDF print, edit, gather stats, settings, logout).

#### Roles and Permissions

Heart and soul of the personnel tracker.

Group:
* Unit - smallest organizational entity. 
* Section - consists of multiple units
* Division - consists of multiple sections

Roles:
* Users - can view their own own profiles can edit personal data to be submitted for approval.
* Leaders - can view the profiles of the organizational group they belong to.
* Staff
  * View/modify the profiles of the group they belong to
  * Approve user requests for editing profile data.
  * Cannot edit or approvte their own requests, must receive approval from a greater entity.
  * Assign/revoke roles to users of a lesser or equal group
  * Cannot assign groups
* Admin - ultimate arbiter of roles and permissions. Cannot view/modify data. Can make other admins.

Examples:
* A section leader can view the profiles of the entire section (including units)
* A section staff can make a unit-level user a leader. Cannot make a section or division level user a leader.
* A division staff can make a section-level user a section staff.
* An admin can make a unit-level user a division-staff, vice versa.
* An admin can elevate a unit staff to section staff (change groups).

Upon termination/outprocessing, a user automatically loses all roles and permissions.

#### Notifications

Think of it like an email inbox, with less functionality.

* Staff and leaders receive a notifification message when a user data-edit request. 
* Approvals happen at the lowest possible level. A unit-level user request would be sent to a section staff.
* Staff have the option to approve or reject the changes. Staff must provide an explanation for rejection.
* Users receive a notification when their request gets approved/rejected.
* All users receives a notification when their role or groups change. 
* Once notifications are read, they get archived after 10 days and deleted after 30 days.
* Users can view archived notifications.

#### Status Reports

A cornerstone feature of the application. Can export an individual profile as a PDF for printing. Individual profiles should have the option to mass download all associated documents as a zip file. 

Organizational reports can contain statistics:

* Number of people on vacation/sick/availability
* NEED MOAR EXAMPLES

#### Uploading Documents

When editing a profile, an upload button next to each data field allows users to provide substantiating documents. New documents uploaded will replace old ones.

#### Export/Import CSV

For excel spreadsheets.

#### Help/FAQ

For users who really can't figure out how to use the web app.

## Mockups

Visual representation of requirements

#### Login
![Login](https://github.com/foodstamp/personneltracker/blob/master/wireframes/login.png)

#### Registration

![Registration](https://github.com/foodstamp/personneltracker/blob/master/wireframes/registration.png)

#### Dashboard

![Dashboard](https://github.com/foodstamp/personneltracker/blob/master/wireframes/dashboard.png)

#### Viewing Notifications

![Notifications](https://github.com/foodstamp/personneltracker/blob/master/wireframes/notifications.png)

#### Setting Roles and Permissions

[Insert Mockup]

#### Organization Summary Statistics

[Insert Mockup]
