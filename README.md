# Spring MVC and Force.com Fulfillment application

This is a simple web application that uses Spring MVC and the Force.com REST API to implement a web service and an HTML front end to accept Invoice Statement IDs, store them locally, and pull invoice details from Force.com.

## Running the application locally

Setup OAuth Remote Access in Salesforce.com

    1. Go to Salesforce.com's Setup page
    2. Go to Develop -> Remote Access
    3. Add a new Remote Access config with a URL of: `http://localhost:8080/_auth`

Add environment variables for authenticating to Salesforce.com (replace the values with the ones from the Remote Access definition on Salesforce.com):

- On Linux/Mac:

        $ export OAUTH_CLIENT_KEY=3MVM3_GuVCQ3gmEE5al72RmBfiAWhBX5O2wYc9zTZ8ytj1E3NF7grV_G99OxTyEcY71Tc46TOvzK_rzoyYYPk
        $ export OAUTH_CLIENT_SECRET=1319558946720906100

- On Windows:

        $ set OAUTH_CLIENT_KEY=3MVM3_GuVCQ3gmEE5al72RmBfiAWhBX5O2wYc9zTZ8ytj1E3NF7grV_G99OxTyEcY71Tc46TOvzK_rzoyYYPk
        $ set OAUTH_CLIENT_SECRET=1319558946720906100

Build with:

    $ mvn clean install

Then run it with:

    $ java -jar target/dependency/webapp-runner.jar target/*.war


## Running on Heroku

Clone this project locally:

    $ git clone git://github.com/jamesward/hello-java-spring-force_dot_com.git

Create a new app on Heroku (make sure you have the [Heroku Toolbelt](http://toolbelt.heroku.com) installed):

    $ heroku login
    $ heroku create -s cedar

Setup OAuth Remote Access in Salesforce.com

    1. Go to Salesforce.com's Setup page
    2. Go to Develop -> Remote Access
    3. Add a new Remote Access config with a URL of: `https://your-app-1234.herokuapp.com/_auth`

Add config params for authenticating to Salesforce.com (replace the values with the ones from the Remote Access definition on Salesforce.com):

    $ heroku config:add OAUTH_CLIENT_KEY=3MVM3_GuVCQ3gmEE5al72RmBfiAWhBX5O2wYc9zTZ8ytj1E3NF7grV_G99OxTyEcY71Tc46TOvzK_rzoyYYPk OAUTH_CLIENT_SECRET=1319558946720906100

Upload the app to Heroku:

    $ git push heroku master

Open the app in your browser:

    $ heroku open

You can deploy the app using this button

<a href="https://heroku.com/deploy?template=https://github.com/Karanraj/spring-mvc-fulfillment-full">
  <img src="https://www.herokucdn.com/deploy/button.png" alt="Deploy">
</a>
