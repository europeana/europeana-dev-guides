# Europeana Java development guidelines

See the [general development guide](general.md) for guidance. Here are additional Java-specific guidelines.


## 1. Your code

### 1.1. Style

* Coding should adhere to the  [Google Java styleguide](https://google.github.io/styleguide/javaguide.html). So this means:
    * Indent with spaces, not tabs
    * One statement per line
    * Braces are used for all <code>if</code>,<code>else</code>,<code>for</code>,<code>do</code> and<code>while</code> 
    statements,     with the opening brace being on the same line as the statement, for example
        <pre>return new MyClass() {
            @Override
            public void method() {
                if (condition()) {
                    try {
                        something();
                    } catch (ProblemException e) {
                        recover();
                    }
                } else if (otherCondition()) {
                    somethingElse();
                } else {
                    lastThing();
                }
            }
        };
        </pre>

* There is one exception where we deviate from the Google Java styleguide; the API team Java projects use 4 spaces for 
indentation instead of 2 (Metis team does use 2 spaces).
* IntelliJ style import is provided [here](https://github.com/google/styleguide/blob/gh-pages/intellij-java-google-style.xml),
Eclipse style import provided [here](https://github.com/google/styleguide/blob/gh-pages/eclipse-java-google-style.xml)<br/>
Note that these are the original Google styles, so indentation is not adjusted (for API team members).

### 1.2. Architecture

See the [general development guide](general.md#13-architecture) for architecture guidance. In addition:
* Use [Maven](https://maven.apache.org/) to build your project
* If your project has sub-projects, create a parent POM file that builds everything, in order
* Use package names that start with <code>eu.europeana</code>


## 2. Software dependencies

### 2.1. Language and framework versions

Develop for the Java and framework versions agreed upon within the team(s). This is currently:
 * Java version 11
 * Spring-Boot 2

### 2.2. Preferred software components

The suggested software components below are in use in other Europeana Java projects and are therefor the preferred 
choices for new Java projects.

* If your app requires a web server, use [Apache Tomcat](http://tomcat.apache.org/).
* If your app requires a database, use either [PostgreSQL](https://www.postgresql.org) or [MongoDB](https://www.mongodb.com)
* If your app requires a search engine, use [Solr](https://lucene.apache.org/solr/)

### 2.2.1 Cloud Foundry
* If the app needs to be deployed on Cloud Foundry (which is usually the case), take into account which web server and
database versions are supported by the [Cloud Foundry Java Buildpack](https://github.com/cloudfoundry/java-buildpack) as
well as by Europeana’s PaaS provider. 

* For production deployments to Cloud Foundry, use a fixed and recent version of the Java Buildpack.

### 2.3. Dependency management

* Managed using [Maven](https://maven.apache.org/)
* Keep dependencies up-to-date by checking for new versions and upgrading regularly
* For important services use the [dependency-check plugin](https://owasp.org/www-project-dependency-check/) frequently 
to check for vulnerabilities.
* Release Europeana libraries and services to our [Artifactory](http://artifactory.eanadev.org/); 
for other code we depend on the public Maven repositories


## 3. Continuous Integration

### 3.1. Automated testing
* Use [JUnit](http://junit.org/) to test features in isolation.
* Analyze the code with the Europeana SonarQube ruleset and make sure that there are: 
    * No blocker and critical issues
    * At least 40% code coverage (preferably 70% or higher)
* Use integration tests where appropriate. If they are part of your project make sure the integration test classes have 
names that end with <code>IT</code> (so we can easily disable them when running test in Jenkins)
* Set up a Jenkins job that builds, tests and analyzes a project regularly 
(either daily, or after each commit to master branch)
* For public-facing services use Runscope tests at the end of a deployment

### 3.2. Semi-automated testing
* Use [JMeter](https://jmeter.apache.org/) or [Blazemeter](https://www.blazemeter.com/) for stress testing new projects
or new features that can have a significant performance impact.

## 4. Documentation

### 4.1. Inline

* Write meaningful JavaDoc
    * When writing a new class always add a description of what it does
    * Strive to document all public methods (that are not simple getters or setters)

