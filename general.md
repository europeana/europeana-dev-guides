# Europeana general development guide

## 1. Your code

### 1.1. License

## License

* Europeana develops open source software licensed under the
  [Europeana Union Public Licence (EUPL v1.2)](https://joinup.ec.europa.eu/collection/eupl/eupl-text-11-12).
* All third-party software used by software developed and distributed by, or on
  behalf of, Europeana must be
  [compatible with the EUPL v1.2](https://joinup.ec.europa.eu/collection/eupl/licence-compatibility).

### 1.2. Version control
* Use [Europeana's Github](https://github.com/europeana)
* Follow ["A successful Git branching model"](http://nvie.com/posts/a-successful-git-branching-model/);
  in summary:
  * Create a **feature branch** for each ticket you work on 
  * Make **atomic commits** with concise but informative messages
  * Create **pull requests** for code changes and let a co-worker review your work
  * Use the **master branch** for production-ready code
  * **Tag releases** in the Git repo once merged into master, using [semantic versioning](http://semver.org/) and use
  those tags to deploy to production.

### 1.3. Architecture

* Software design should follow as far as is practical the [12-factor methodology](http://12factor.net/).
* App configuration should come from environment variables.
  * In Cloud Foundry environments (testing, acceptance and production), use `cf set-env`.
  * Document an app's environment variables in its Git repo's README.
* Modularise and package distinct & reusable functions into libraries, i.e. Ruby
  gems or Java jars
  
### 1.4. Selecting third-party libraries and frameworks
Prefer software that:
* Has an active community (e.g. on GitHub)
* Provides new releases and fixes regularly
  
### 1.5. Accessibility

* Where practical, all functionality should be available in static HTML with
  JavaScript disabled
* UX can be improved with JavaScript, IAX, etc
* The front-end layout and presentation (if there is any) should use Europeana's styleguide.

## 2. Continuous Integration

### 2.1. Automated testing
* Use the language-specific testing framework to describe and test features (i.e. unit and integration tests)
* Use Github's web hooks to run automated tests on code changes in pull requests; at least:
  * [Travis CI](https://travis-ci.org/) to run your test suite
  * [Coveralls](https://coveralls.io/) or similar to check code coverage

### 2.2. Test environment

* Deploy the develop branch of your code to a test space in the intended
  production environment.
* Use our Jenkins service to deploy.

## 3. Deployment to production

* Set up a Jenkins job that deploys your project to the desired server (usually Cloud Foundry)
* For the deployment of front-facing production services make sure this Jenkins job includes:
    * Blue/green deployment
    * Sending all access logs and logs of INFO level and higher to the Europeana ELK stack
    * Sending data to the Europeana APM
* Make sure uptime is measured with Pingdom

## 4. Documentation

### 4.1. End user

* Maintain in the repo root at least README.md and LICENSE.md.
* Use Markdown for any documentation included in the repo.
* Additional end user documentation should be published in the Github wiki.
