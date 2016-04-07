# Europeana Java development guide

See the [general development guide](general.md) for guidance. Here are additional Java-specific guidelines.

## 1. Your code

### 1.1. Style

* Coding conventions are based on the [Google-provided styleguide](https://google.github.io/styleguide/javaguide.html)
* Eclipse style import provided [here](https://google-styleguide.googlecode.com/svn/trunk/eclipse-java-google-style.xml)

### 1.2. Architecture

See the [general development guide](https://github.com/europeana/europeana-dev-guides/blob/develop/general.md#14-architecture) for architecture guidance. In addition:
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
  * Those specified in the [general guide](https://github.com/europeana/europeana-dev-guides/blob/develop/general.md#31-automated-testing)

## 4. Documentation

### 4.1. Inline

* Use JavaDoc
