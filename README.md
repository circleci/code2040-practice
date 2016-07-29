heroku-cd
=========

This project is an example of an application that can be continuously delivered to Heroku through a pipeline based on staging and production environments.

##Installing and running locally
* Clone the repo
* Run `pip install -r requirements.txt` (preferably inside a virtualenv) to install the dependencies
* Run `foreman start [-p port]` to run the “hello” app locally
* Run `nosetests` to run the unit test
* Refer to the [Heroku docs](https://devcenter.heroku.com/articles/getting-started-with-python) for information on deploying to Heroku from the command line

##Deployment with CircleCI
First, sign up for [CircleCI](https://circleci.com/) if you haven’t already, fork the repo, and follow it from CircleCI.
There is [a detailed doc](https://circleci.com/docs/continuous-deployment-with-heroku) in the CircleCI docs about deployment to Heroku. But the three simple steps you need to perform are:

1. Enter your Heroku API key in the “Heroku” section of the settings for your project on CircleCI
2. Setup an SSH key for deployment to Heroku (CircleCI makes this very easy)
3. Configure your circle.yml file to deploy to Heroku. See circle.yml file in this project for an example (you will need to choose different app names depending on what your apps are called in Heroku).

##The Continuous Delivery Pipeline
This project implements continuous delivery with a pipeline based on “staging” and “master” branches that correspond to “staging” and “prod” heroku environments respectively. Feature branches that are ready to merge can first go into staging, where they will built by CircleCI and automatically deployed to the Heroku staging environment. Once deployed to staging, any number of automated or even manual tests can be run before merging into master to push new features into production. Each merge is performed manually in this project, but the merge from staging to master, for example, could be automated.

##See Also
* [CircleCI](https://circleci.com/)
* The [virtualenv](http://virtualenv.readthedocs.org/en/latest/) and [virtualenvwrapper](http://virtualenvwrapper.readthedocs.org/en/latest/) docs
* [Getting Started with Python on Heroku](https://devcenter.heroku.com/articles/getting-started-with-python) and [Managing Multiple Environments for an App](https://devcenter.heroku.com/articles/multiple-environments) articles from the [Heroku Dev Center](https://devcenter.heroku.com/)
* [Testing Flask Applications](http://flask.pocoo.org/docs/testing/) from the Flask docs
* [The nose documentation](https://nose.readthedocs.org/en/latest/) for more information about the nose test runner
* [Continuous Deployment with Heroku](https://circleci.com/docs/continuous-deployment-with-heroku) from the CircleCI docs.
