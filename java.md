# Europeana Java development guide

## 1. Your code

### 1.1. Style

* Coding conventions are based on the [Google-provided styleguide](https://google.github.io/styleguide/javaguide.html)
* Eclipse style import provided [here](https://google-styleguide.googlecode.com/svn/trunk/eclipse-java-google-style.xml)

### 1.2. License

* Europeana develops open source software licensed under the [Europeana Union Public Licence (EUPL v.1.1)](https://joinup.ec.europa.eu/community/eupl/og_page/european-union-public-licence-eupl-v11).
* All third-party software used by software developed and distributed by
  Europeana must be [compatible with the EUPL v.1.1](https://joinup.ec.europa.eu/software/page/eupl/eupl-compatible-open-source-licences).

### 1.3. Version control
* Use [Europeana's Github](https://github.com/europeana)
* Follow ["A successful Git branching model"](http://nvie.com/posts/a-successful-git-branching-model/);
  in summary:
  * Make **atomic commits** with concise but informative messages
  * Use the **develop branch** for ongoing development
  * Use the **master branch** for production-ready code
  * Create **pull requests** for code changes
  * **Tag releases** in the Git repo once merged into master, using [semantic versioning](http://semver.org/)

### 1.4. Architecture

* Software design should follow as far as is practical the [12-factor methodology](http://12factor.net/).
* App configuration should come from environment variables.
  * In Cloud Foundry environments (testing, acceptance and production), use `cf set-env`.
  * Document an app's environment variables in its Git repo's README.
* Modularise and package distinct & reusable functions into libraries, i.e. Java jars
* Use [Maven](https://maven.apache.org/) to build your project
* If your project has sub-projects, create a parent POM file that builds everything, in order

## 2. Software dependencies

### 2.1. Language and framework versions

* Develop for the latest stable versions of Java supported by the intended production environment and any other dependencies.

### 2.2. Preferred software components

The suggested software components below are in use in other of Europeana's Java projects, and are the preferred choices for new Java projects.

#### 2.2.1. Web server

If your app requires a web server, use [Apache Tomcat](http://tomcat.apache.org/).

#### 2.2.2. Database

If your app requires a database, use either PostgreSQL or MongoDB.

### 2.3. Design

The front-end layout and presentation should use Europeana's styleguide

### 2.4. Dependency management

* Managed using [Maven](https://maven.apache.org/)
* Keep your dependencies up-to-date over time

## 3. Continuous Integration

### 3.1. Automated testing
* Use [JUnit](http://junit.org/) to test features (i.e. unit and integration tests)
* Use Github's web hooks to run automated tests on code changes in pull requests; at least:
  * [Travis CI](https://travis-ci.org/) to run your test suite
  * [Coveralls](https://coveralls.io/) to check code coverage

### 3.2. Test environment

* Deploy the develop branch of your code to a test space in the intended production environment.
* Use our Jenkins service to deploy.

## 4. Documentation

### 4.1. Inline

* Use JavaDoc

### 4.2. End user

* Maintain in the repo root at least README.md and LICENSE.md.
* Use Markdown for any documentation included in the repo.
* Additional end user documentation should be published in the Github wiki.
