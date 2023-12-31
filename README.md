# Open Certification Trainer
This is a website for assisting in training for certifications.
It was built using the awesome React framework.

## Purpose
When having to learn for certifications, it is often useful to use multiple choice questions, as they are a common certification format.
This website is able to host courses with questions and their corresponding answers.

You can view them and take assessments, where your knowledge is checked.
More and more functions will be coming as the project progresses.

## Features
- Certification Management (Create, Edit)
- User Management
- Post (News) Management
- Learn using overview modes
- Train using assessment mode
- Find your weaknesses using session history and charts

## Installation
This project was tested on Arch Linux, Ubuntu and Windows 10.
You'll need to have [NodeJS](https://nodejs.org/en/) and [PostgreSQL](https://www.postgresql.org/) installed. For NodeJS, the latest LTS version is recommended, which is 8.9.4 at the time of writing. PostgreSQL should be used in at least version 10.1.

Clone the project, navigate to the project folder using your PowerShell/Bash

`npm install`

Once this installed all packages, you can edit the .env.config, where you'll have to update the database user login settings for your environment. For production use, you should generate some key for usage as your own JWT secret.
When done, you can start the website by running

`npm start`.

Afterwards the site can be accessed on http://localhost:8080. 

If you're receiving an error like 

```js
const { token } = req.cookies;

SyntaxError: Unexpected token {
```

you should consider updating your node server. As described above, we recommend using the latest LTS version, which is 8.9.4 at the time of writing.

You can also configure the site to be accessed using a DNS name.
Use the CERT_TRAINER_VHOST variable and set it to the domain name you'd like.
Afterwards make sure to edit the /etc/hosts file (Linux + Windows) on your host server.
If you plan on using this tool in your company, you need to configure your company's DNS server to redirect to your host server for the domain you configured.

## Create an admin user

Credential default is `root:root`

```
psql -U postgres -h localhost -d postgres
postgres-# show schemas\dn;
postgres-# \du
postgres-# \dn open_certification_trainer;
postgres=# select * from open_certification_trainer."user";
postgres=# update open_certification_trainer."user" set is_admin=true where user_name='test';
```

## Courses
Courses can be imported using the Certification Management page.
You can press "Create New Certification" and then either enter your certification manually or import a JSON file.
For the format of your courses, please take a look at the demoCert.json file in the project root.
IDs for the certification, questions and answers don't have to be set in your import file, they will be generated automatically if they're missing.

## Impressions
### Sign Up
![signup](https://user-images.githubusercontent.com/4287938/34416337-487fabb4-ebf3-11e7-8e28-dfa8ed40b05c.gif)

### Log In
![login](https://user-images.githubusercontent.com/4287938/34416333-482f4016-ebf3-11e7-8079-4220be37c31d.gif)

### Study
Select a certification / course and take a look at the questions contained including the correct answers.
![study](https://user-images.githubusercontent.com/4287938/34416338-4899c27e-ebf3-11e7-9fc7-672fe357ac2e.gif)

### Train
Take an assessment for a certification. You will have to answer all questions contained in the course, but questions and answers are shuffled. Once you're done, the course will be regarded as passed, if you answered 70% or more of the questions correctly.
![train](https://user-images.githubusercontent.com/4287938/34416339-48b35efa-ebf3-11e7-8988-43d3074c45c9.gif)

### Check your learning progress
![check](https://user-images.githubusercontent.com/4287938/34416332-48137fa2-ebf3-11e7-8650-13ee45e2c416.gif)

### GUI Management of Certifications
![management](https://user-images.githubusercontent.com/4287938/34416334-484b4c70-ebf3-11e7-8152-c3119cfaf359.gif)

### Post / News Management
![posts](https://user-images.githubusercontent.com/4287938/34416335-48645b20-ebf3-11e7-9b6e-d98a6eb882cf.gif)

## License
Licensed using the MIT license, happy learning!
