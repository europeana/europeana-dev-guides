# Europeana Ruby development guide

See the [general development guide](general.md) for guidance. Here are additional Ruby-specific guidelines.

## 1. Your code

### 1.1. Style

* Coding conventions are based on the [Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide),
  with some variations.
* The style is specified in a Rubocop configuration file: [.ruby-style.yml](ruby/.ruby-style.yml).

### 1.2. Architecture
See the [general development guide](https://github.com/europeana/europeana-dev-guides/blob/develop/general.md#14-architecture) for architecture guidance. In addition:
* In development environments, use the [dotenv](https://github.com/bkeepers/dotenv)
    gem and set these in .env in your application root.
* If your app has multiple process roles, list these in a [Procfile](https://docs.cloudfoundry.org/buildpacks/ruby/ruby-prod-server.html),
  and in dev environments, use (foreman)[https://github.com/ddollar/foreman]
  to start all processes.

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
  * Those specified in the [general guide](https://github.com/europeana/europeana-dev-guides/blob/develop/general.md#31-automated-testing)
  * [Hound CI](https://houndci.com/) to check code style
  * [Hakiri](https://hakiri.io/) to check code security

## 4. Documentation

### 4.1. Inline

* Use [YARD](http://yardoc.org/) & Markdown.
