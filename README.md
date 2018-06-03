# node-password-recovery

## Description
A sample of how to build a password recovery workflow with node js.

## Enviroment Variables
Before it is ready to use, there are two environment variables which have to be set up:

    * process.env.NODEMAILER_EMAIL => This is the email adress which should be used
    * process.env.NODEMAILER_PASS  => This is the password for the email account which should be used

Other Enviroment Variables which are predefined with standard values are:
    
    * process.env_PORT          => Port at which the node server listens (default: 3000)
    * process.env_IP            => IP adress which the node server listens (default: localhost or 127.0.0.1)
    * process.env.MONGODBPORT   => MongoDB Port which should be used (default: 27017)

## MongoDB Database and User Model
For storing and testing, a mongoDB Database with the name **pwRecoverTest** will be created at first run of app.js.
A User model file is stored at ./models/user.js
Fit or replace it with your needs.
Four fields are important to make this code work:

    1. email
    2. password
    3. resetPasswordToken
    4. resetPasswordExpires

## Database Seed file
For easier testing this standalone code, a seeds file is included. It's located under ./seeds.js and nearly ready to use.
To send test emails, you have to make changes to at least on line 12 where it says:

    ```javascript
    email: "FILL IN YOUR TEST EMAIL ADRESS"
    ```

Replace **FILL IN YOUR TEST EMAIL ADRESS** with an email adress which you own for testing purpose.

## Recovery Email
The package [nodemailer](https://www.npmjs.com/package/nodemailer) is used to send recovery and success Emails for password reset to the Users which are found in the Database when they try to recover the password.
The option to send mails through Gmail is hardcoded right now.
If you want to use another one, I refere to look at [https://nodemailer.com/](https://nodemailer.com/about/) to get the information, which ones are supported and how you have to define it.

To make things simpler, you only have to change it in the function `sendMailOut` at line 104.

## Server Side Content delivery through EJS Template engine.
To make this code not only working but also view able, a sample html content is delivered through EJS Templates which are generated by the node server.

To use it with other Front-End Frameworks, replace all `res.render(...)` statements with that kind of response which is usable for your project. For example replace it with `res.status(200).json(...)` and handle everything else on the Front-End. 

## Debug Outputs via console.logs
Every console.log which you found in the codebase, has the task to give you feedback on th server side. Because this codebase is a sample, i leave each console.log there.
Feel free to delete them :-D.

## Last but not Least
This is version 1.0
Nothing like checking for malicious code, fun inputs or something like that is done so far.
Please don't forget to check the user inputs before you go life.



