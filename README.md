# Overview #
This is a skeleton for anyone looking to get up and running Angular2 and TypeScript to build a SPA with AngularJS 2 
and RESTful API with Node.js, ORM with Sequelize.

# Tech Stacks #

- Frontend
    - [Angular 2](https://angular.io/)
    - [TypeScript](https://www.typescriptlang.org/)
    - [Webpack](https://webpack.github.io/)
    - [Jasmine - test framework](https://jasmine.github.io/)
    - [Karma - test runner](https://karma-runner.github.io/1.0/index.html)
    - [Istanbul - code coverage](https://istanbul.js.org/)
    - [Protractor - end to end testing](http://www.protractortest.org/#/)
    - [SASS - css preprocessor](http://sass-lang.com/)

- Backend
    - [Node.js](https://nodejs.org/en/)
    - [JavaScript + ES6](http://es6-features.org/)
    - [Sails.js](http://sailsjs.com/)
    - [Sequelize - ORM](http://docs.sequelizejs.com/en/v3/)
    - [Passport - OAuth2 and Social authentication](https://www.npmjs.com/package/passport)
    - [Mocha - test framework for Node.js](https://mochajs.org/)
    - [Mocha istanbul- code coverage](https://www.npmjs.com/package/grunt-mocha-istanbul)
    - [Chai - test assertion](http://chaijs.com/)
    - [PM2 - production process manager for Node.js](http://pm2.keymetrics.io/)
    - [Keymetrics - optional process for monitering Node process](https://keymetrics.io/)

- DevOps
    - [Docker](https://www.docker.com/)
    - [Docker compose](https://docs.docker.com/compose/)
- Continuous Integration & Continuous Deployment / Delivery (CI/CD)
    - [Jenkins](https://jenkins.io/)
    - [AWS Elastic Beanstalk - single / multiple containers‎](https://aws.amazon.com/elasticbeanstalk/?sc_channel=PS&sc_campaign=acquisition_RU&sc_publisher=google&sc_medium=english_english_beanstalk_b&sc_content=elastic_beanstalk_e&sc_detail=aws%20elastic%20beanstalk&sc_category=beanstalk&sc_segment=165215078773&sc_matchtype=e&sc_country=VN&s_kwcid=AL!4422!3!165215078773!e!!g!!aws%20elastic%20beanstalk&ef_id=WJrmfAAABanXmkOX:20170309113727:s)
    - [AWS EC2 Container Registry](https://aws.amazon.com/ecr/)

**Here are its features:**

* The best practice in directory/file organization for Angular and Node projects.
* Ready to go build system using Webpack 2 for working with TypeScript.
* Testing code Angular 2 with Jasmine and Karma.
* Testing code Node with Mocha and Chai.
* Coverage with Istanbul and Karma.
* End-to-end Angular with Protractor.
* Predefined ORM configuration using Sequelize with Sails and MySQL adapter by default.
* Contains a set of common functions to develop Angular 2 and Node.js applications. Such as cross cutting module for
caching, exception handling, logging, mailing, utilities.
* Predefined the docker file and docker compose to build, run, ship, and deploy your applications anywhere (VM, Docker Cloud, Azure, AWS, etc.).

# Installing Dependencies #

Make sure you have Node version >= 6.9.1 and NPM >=3 installed. Then run the folowing commands to install all needed dependencies
```sh
# Install all dependencies to run the app
sudo cd scripts && chmod +x setup.sh && ./setup.sh

# E2e testing
sudo cd scripts && chmod +x setup-e2e.sh && ./setup-e2e.sh
```

# Configuration #
## Server Configuration ##
**Environment.env configuration**

To run the server, you have to define an *environment.env* file and drop in *src/server/bin* directory.
This configuration should only container sensitive information such as database connection string, secret key.
The application support encript the content of this file if you drop a *secret.dat* in th *src/server* directory.

Below is the sample configuration file (each key should be in a new line base on running OS)

```
NODE_ENV=development
PORT=1337
OAUTH2_SECRET=your key
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_DATABASE_NAME=your-db-name
MYSQL_USERNAME=your username
MYSQL_PASSWORD=your password
SES_ACCESS_KEY=aws-key
SES_SECRET_ACCESS_KEY=aws-access-key
FACEBOOK_CLIENT_ID=facebook-client-id
FACEBOOK_CLIENT_SECRET=facebook-secret-key
GOOGLE_CLIENT_ID=google-client-id
GOOGLE_CLIENT_SECRET=google-secret-key
```

**Environment settings**

You can change the configuration for a specific environent by changing the environment_name.js file in *src/server/src/config/env* directory.

## Client Configuration ##
You can change the webpack, testing, and end to end configurations in the *src/client/config* directory

# Running the app #
```sh
# Start Angular Webpack dev server and Node API - Windows
npm start

# For Linux OS, please run both commands separately

# Start API with node-dev
npm run api:dev

# Start Webpack Dev Server
npm run ui

# Start with PM2
npm install pm2 -g
cd src/server
pm2 start pm2-process.yml

# By default, we run 2 PM processes, if you want to scale, run below command
pm2 scale commission-royalty-app <number>

```
go to [http://localhost:3000](http://localhost:3000) in your browser to access Angular app.
You also can access Node API at [http://localhost:1337](http://localhost:1337)

# Tasks #

## Analyze code ##
Analyze code using TSLint and ESLint rules
```sh
# Analyze Angular and Node code
npm run analyze

# Analyze Angular code
npm run analyze:tslint

# Analyze Node code
npm run analyze:eslint
```

## Unit Test ##
```sh
# Test Angular code
npm test

# Test Node API
npm run test:api
```

## End-to-end test ##
Run e2e testing with Protractor
```sh
# Start Selenium server
webdriver-manager start

# Run with Chrome browser
npm run e2e:chrome

# Run with Firefox browser
npm run e2e:firefox

# Run with IE browser
npm run e2e

# Run with PhantomJS browser. Recommand using for CI/CD process
npm run e2e:phantomjs
```

## Build release package (include Angular and Node) ##
```sh
# Build Angular code and prepare release pacakge
npm run release
```

## Build docker ##
```sh
# Build docker images including web and api
npm run build:docker

# Change work dir to the dist directory where the docker-compose.yml located and run below command
docker-compose build
docker-compose up
```

go to [http://localhost](http://localhost) to access Angular app and [http://localhost/api](http://localhost/api) to access Node API

# Coding Styles #
We use the TSLint and ESLint to analyze the code by using the following styles
- Angular 2 Style [https://angular.io/styleguide](https://angular.io/styleguide)
- ESLint for JavaScript [http://eslint.org/docs/rules/](http://eslint.org/docs/rules/)
- TSLint for TypeScript [https://palantir.github.io/tslint/rules/](https://palantir.github.io/tslint/rules/)
- Microsoft Style [https://github.com/Microsoft/tslint-microsoft-contrib](https://github.com/Microsoft/tslint-microsoft-contrib)


# Sample CI/CD Pipeline #
![Alt text](https://github.com/stormit-vn/ag2-sails-devops-starter/blob/master/cicd-pipeline.jpg?raw=true "CI/CD Pipeline")


# ☑ TODO
- [ ] Support Conditional Request for API
- [ ] Support NoSQL i.e. MongoDB
- [ ] Support more cacher options such as Memcached / Redis
- [ ] AWS CloudFormation script to setup infrastructure automatically
- [ ] Apply NgRedux
- [ ] An alternative option to host with NGINX






