# Europeana Ruby development guide

## 1. Your code

### 1.1. Style

* Coding conventions are based on the [Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide),
  with some variations.
* The style is specified in a Rubocop configuration file: [.ruby-style.yml](ruby/.ruby-style.yml).

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
  * In development environments, use the [dotenv](https://github.com/bkeepers/dotenv)
    gem and set these in .env in your application root.
  * In Cloud Foundry environments (testing, acceptance and production), use `cf set-env`.
  * Document an app's environment variables in its Git repo's README.
* Modularise and package distinct & reusable functions into libraries, i.e. Ruby
  gems
* If your app has multiple process roles, list these in a [Procfile](https://docs.cloudfoundry.org/buildpacks/ruby/ruby-prod-server.html),
  and in dev environments, use (foreman)[https://github.com/ddollar/foreman]
  to start all processes.

### 1.5. Accessibility

* Where practical, all functionality should be available in static HTML with
  JavaScript disabled
* UX can be improved with JavaScript, IAX, etc

## 2. Software dependencies

### 2.1. Language and framework versions

* Develop for the latest stable versions of Ruby and Rails supported by the
  intended production environment and any other dependencies.
* Declare the Ruby version in your project's Gemfile or .ruby-version
* In dev environments, it is recommended to use RVM or rbenv to install required
  Ruby versions.

### 2.2. Preferred software components

The suggested software components below are in use in other of Europeana's
Ruby projects, and are the preferred choices for new Ruby projects.

#### 2.2.1. Web server

If your app requires a web server, use [Puma](https://github.com/puma/puma).

#### 2.2.2. Database

If your app requires a database, use either PostgreSQL or MongoDB.

#### 2.2.3. Background jobs

If your app needs to run background jobs, use [Delayed::Job](https://github.com/collectiveidea/delayed_job).

#### 2.2.4. Task scheduler (cron-like)

If your app needs to schedule tasks, use [clockwork](https://github.com/tomykaira/clockwork).

### 2.3. Design

The front-end layout and presentation should use [Europeana's styleguide](https://github.com/europeana/europeana-styleguide-ruby).

### 2.4. Dependency management

* Managed using [Gem Bundler](http://bundler.io/).
* Keep your dependencies up-to-date over time, monitoring them with [Gemnasium](http://gemnasium.com/).
* If your app needs to get data from Europeana’a REST API, use our own [europeana-api](https://github.com/europeana/europeana-api-client-ruby) gem


## 3. Continuous Integration

### 3.1. Automated testing
* Use RSpec or Minitest to describe and test features (i.e. unit and integration tests)
* Use fixtures (not factories)
* Use Github's web hooks to run automated tests on code changes in pull requests; at least:
  * [Hound CI](https://houndci.com/) to check code style
  * [Hakiri](https://hakiri.io/) to check code security
  * [Travis CI](https://travis-ci.org/) to run your test suite
  * [Coveralls](https://coveralls.io/) to check code coverage

### 3.2. Test environment

* Deploy the develop branch of your code to a test space in the intended
  production environment.
* Use our Jenkins service to deploy.

## 4. Documentation

### 4.1. Inline

* Use [YARD](http://yardoc.org/) & Markdown.

### 4.2. End user

* Maintain in the repo root at least README.md and LICENSE.md.
* Use Markdown for any documentation included in the repo.
* Additional end user documentation should be published in the Github wiki.
