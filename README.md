# Rails Blueprint
A starter blueprint to help fast track setting up a new Rails application.

## Getting Started
To get started, simply clone this repo into a folder with the name of your application. 

<details>
  <summary>Clone Repo</summary>

  Replace `my_app` with the name of your application.
  ```clone
  git clone https://github.com/dalezak/rails-blueprint.git my_app
  ```
</details>

Then move through the list below doing any of the sections your application needs. If you already have Rails setup, then skip the `Setup Environment` section, or if you don't want `Soft Deletes` just move past it.

## Setup Environment
Setup your local environment with Ruby, Rails and Node.
<details>
  <summary>Install Ruby</summary>

  Visit [Rails > Getting Started > Installing Ruby](https://guides.rubyonrails.org/getting_started.html#installing-ruby) for instructions on installing the Ruby language.

  ```console
  ruby -v 
  ```
</details>

<details>
  <summary>Install RVM</summary>

  Visit [RVM > Install](https://rvm.io/rvm/install) for instructions on setting up RVM so you can easily switch between different version of Ruby.

  ```console
  rvm --default use 3.0.0 
  ```
</details>

<details>
  <summary>Install Node</summary>

  Visit [Rails > Getting Started > Installing Node](https://guides.rubyonrails.org/getting_started.html#installing-node-js-and-yarn) for instructions on setting up Node and Yarn.

  ```console
  npm -v
  ```
  
  ```console
  yarn -v
  ```
</details>

<details>
  <summary>Install Rails</summary>

  Visit [Rails > Getting Started](https://guides.rubyonrails.org/getting_started.html#creating-a-new-rails-project-installing-rails-installing-rails) for instructions on installing Rails framework.

  ```console
  gem install rails -v 7.0.0
  ```
  
  ```console
  rails -v
  ```
</details>

## Install Database
Install a local database.
<details>
  <summary>Install Postgres</summary>

  Visit [Postgres > Download](https://www.postgresql.org/download/macosx/) for instructions on installing Postgres database.

  ```console
  psql --version
  ```
</details>

_-or-_

<details>
  <summary>Install SQLite3</summary>

  Visit [Rails > Getting_started > Installing SQLite](https://guides.rubyonrails.org/getting_started.html#installing-sqlite3) for instructions on installing SQlite database.
</details>

## Create Project
Run `rails new --help` to view all command options.

<details>
  <summary>Postgres + Bootstrap + Esbuild</summary>

  Creates a new Rails project with Postgres database, Bootstrap css and ESbuild javascript.
  ```console
  rails new . -s --git --database=postgresql --css=bootstrap --javascript=esbuild
  ```
</details>

_-or-_

<details>
  <summary>Postgres + Bootstrap + Webpack</summary>

  Creates a new Rails project with Postgres database, Bootstrap css and Webpack javascript.
  ```console
  rails new . -s --git --database=postgresql --css=bootstrap --javascript=webpack
  ```
</details>

_-or-_

<details>
  <summary>Postgres + Bootstrap + Rollup</summary>

  Creates a new Rails project with Postgres database, Bootstrap css and Rollup javascript.
  ```console
  rails new . -s --git --database=postgresql --css=tailwind --javascript=rollup
  ```
</details>

## Migrate Database
After creating your Rails project, you'll need to run `rails db:create` to create the local database.

## User Authentication
Setup authentication so that users can login to your application.

<details>
  <summary>Setup Devise</summary>

  [Devise](https://github.com/heartcombo/devise) is flexible authentication solution for Rails with Warden.

  [This template](https://railsbytes.com/templates/X8Bsjx) adds user authentication to your app using the Devise gem. 
  ```console
    rails app:template LOCATION="https://railsbytes.com/script/X8Bsjx"
  ```
  Installation Questions:
  - What do you want to call your Devise model? `User`
  - Do you want to any extra attributes to User? `y`
  - What attributes? `name` _# use comma separated list of attributes_

  Post Installation Steps:
  1. In `config/environments/development.rb`, add `config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }`
  2. Migrate Database:
  ```console
  rails db:migrate
  ```

  Learning More:
  - [Configuring Models](https://github.com/heartcombo/devise#configuring-models)
  - [Configuring Views](https://github.com/heartcombo/devise#configuring-views)
  - [Controller Filters](https://github.com/heartcombo/devise#controller-filters-and-helpers)
  - [Configuring Routes](https://github.com/heartcombo/devise#configuring-routes)
  - [GoRails Tutorial](https://gorails.com/episodes/user-authentication-with-devise)
</details>

## User Authorization
Setup authorization so you can protect resources based on user roles.

<details>
  <summary>Setup CanCanCan</summary>

  [CanCanCan](https://github.com/CanCanCommunity/cancancan) is authorization Gem for Ruby on Rails.

  [This template](https://railsbytes.com/templates/V33sj3) add CanCanCan gem and generates default abilities file. 
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/V33sj3'
  ```

  Learning More:
  - [Defining Abilities](https://github.com/CanCanCommunity/cancancan#define-abilities)
  - [Checking Abilities](https://github.com/CanCanCommunity/cancancan#check-abilities)
  - [Controller Helpers](https://github.com/CanCanCommunity/cancancan#controller-helpers)
  - [Developer Guide](https://github.com/CanCanCommunity/cancancan/blob/develop/docs/README.md)
  - [GoRails Tutorial](https://gorails.com/episodes/authorization-with-cancancan)
</details>

## Single Sign On
Allows users the ability to login to your application through other services like Google.

<details>
  <summary>Setup Omniauth</summary>

  [Omniauth](https://github.com/omniauth/omniauth) is a flexible authentication system utilizing Rack middleware. 

  [This template](https://railsbytes.com/templates/xkjsK3) adds Omniauth gem, creates sessions, registrations and omniauth controllers
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/xkjsK3'
  ```

  Post Installation Steps:
  1. Add Omniauth routes to  `config/routes.rb`
  ```console
  devise_for :users,
    controllers: {
      sessions: "sessions",
      registrations: "registrations",
      omniauth_callbacks: "omniauth",
    }
  ```

  Learning More:
  - [Getting Started](https://github.com/omniauth/omniauth/wiki#getting-started)
  - [GoRails Tutorial](https://gorails.com/episodes/omniauth-twitter-sign-in)
</details>

## Soft Deletes
Provide soft delete functionality so you have ability to un-delete records.

<details>
  <summary>Setup Paranoia</summary>

  [Paranoia](https://github.com/rubysherpas/paranoia) provides soft deletes functionality to ActiveRecord.

  [This template](https://railsbytes.com/templates/Xg8s3J) installs the Paranoia gem for soft deletes.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/Xg8s3J'
  ```

  Learning More:
  - [Migrate Models](https://github.com/rubysherpas/paranoia#run-your-migrations-for-the-desired-models)
  - [Model Usage](https://github.com/rubysherpas/paranoia#usage)
  - [GoRails Tutorial](https://gorails.com/episodes/soft-delete-with-paranoia)
</details>

_-or-_

<details>
  <summary>Setup Discard</summary>

  [Discard](https://github.com/jhawthorn/discard), soft deletes for ActiveRecord done right.

  [This template](https://railsbytes.com/templates/z0gsEQ) installs the Discard gem for soft deletes.
  ```console
  rails app:template LOCATION='https://railsbytes.com/templates/z0gsEQ'
  ```

  Learning More:
  - [Migrate Models](https://github.com/jhawthorn/discard#usage)
  - [Discard Record](https://github.com/jhawthorn/discard#discard-a-record)
  - [Undiscard Record](https://github.com/jhawthorn/discard#undiscard-a-record)
  - [Default Scopes](https://github.com/jhawthorn/discard#default-scope)
</details>

## Image Uploads
Add file uploads instead of using the ActiveStorage functionality/

<details>
  <summary>Setup Shrine</summary>

  [Shrine](https://github.com/shrinerb/shrine) is a modular file upload toolkit that allows direct uploads to S3, resumable uploads, image processing and more.

  [This template](https://railsbytes.com/templates/xYasLK) installs Shrine gem, config initializer, plus adds some handy uploaders you can use.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/xYasLK'
  ```
</details>

## Project Configuration
Some handy project configurations to make your life simpler.

<details>
  <summary>Setup Figaro</summary>

  [Figaro](https://github.com/laserlemon/figaro) is simple Heroku-friendly configuration using ENV and a single YAML file.

  [This template](https://railsbytes.com/templates/VRZs9V) adds Figaro for simple configuration using ENV and a single YAML file.
  ```console
  rails app:template LOCATION="https://railsbytes.com/script/VRZs9V"
  ```
</details>

<details>
  <summary>Setup Rubocop</summary>

  [Rubocop](https://github.com/rubocop/rubocop-rails) is an extension focused on enforcing Rails best practices and coding conventions.

  [This template](https://railsbytes.com/templates/XE5sl5) adds rubocop to your Rails app.
  ```console
  rails app:template LOCATION="https://railsbytes.com/script/XE5sl5"
  ```
</details>

<details>
  <summary>Setup Better Errors</summary>

  [Foreman](https://github.com/BetterErrors/better_errors) is better error page for Rack apps.

  [This template](https://railsbytes.com/templates/V33s0D) adds Better Errors and Binding of Caller gems.
  ```console
  rails app:template LOCATION="https://railsbytes.com/script/V33s0D"
  ```
</details>

<details>
  <summary>Improve Seeds Folder</summary>

  Organize your seeds files into environment folders and execute them in alphanumeric order.

  [This template](https://railsbytes.com/templates/xGqsmL) sets up environment specific seeds folders.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/xGqsmL'
  ```
</details>

<details>
  <summary>Clear Development Logs</summary>

  Automatically clear development logs when they get over 2mb.

  [This template](https://railsbytes.com/templates/VZgs77) adds an initializer to clear development logs.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/VZgs77'
  ```
</details>

<details>
  <summary>GitHub Issue Templates</summary>

  Creates bug reports, feature requests and code maintenance issue templates in GitHub.

  [This template](https://railsbytes.com/public/templates/XvEs4K) adds some handy GitHub issue templates.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/XvEs4K'
  ```
</details>

<details>
  <summary>GitHub Pull Request Template</summary>

  Creates a pull request template for GitHub.

  [This template](https://railsbytes.com/public/templates/VdrsPl) add a GitHub pull request template.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/VdrsPl'
  ```
</details>

## Other Templates
Visit [railsbytes.com](https://railsbytes.com/public/templates) for other handy templates to help setup your environment.

## Rails Tutorials

If you are looking for Rails tutorials, I'd highly recommend you checkout [gorails.com](https://gorails.com) and [driftingruby.com](https://www.driftingruby.com), both great resources for learning Rails.
