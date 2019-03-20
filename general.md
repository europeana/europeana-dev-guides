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
  * Make **atomic commits** with concise but informative messages
  * Use the **develop branch** for ongoing development
  * Use the **master branch** for production-ready code
  * Create **pull requests** for code changes
  * **Tag releases** in the Git repo once merged into master, using [semantic versioning](http://semver.org/)

### 1.3. Architecture

* Software design should follow as far as is practical the [12-factor methodology](http://12factor.net/).
* App configuration should come from environment variables.
  * In Cloud Foundry environments (testing, acceptance and production), use `cf set-env`.
  * Document an app's environment variables in its Git repo's README.
* Modularise and package distinct & reusable functions into libraries, i.e. Ruby
  gems or Java jars

### 1.4. Accessibility

* Where practical, all functionality should be available in static HTML with
  JavaScript disabled
* UX can be improved with JavaScript, IAX, etc

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

## 3. Documentation

### 3.1. End user

* Maintain in the repo root at least README.md and LICENSE.md.
* Use Markdown for any documentation included in the repo.
* Additional end user documentation should be published in the Github wiki.
