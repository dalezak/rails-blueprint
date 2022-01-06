# Rails Blueprint
> A starter blueprint for fast tracking Rails development

## Setup Environment
<details>
  <summary>Install Ruby</summary>

  [https://guides.rubyonrails.org/getting_started.html#installing-ruby](https://guides.rubyonrails.org/getting_started.html#installing-ruby)

  ```console
  ruby -v 
  ```
</details>

<details>
  <summary>Install RVM</summary>

  [https://rvm.io/rvm/install](https://rvm.io/rvm/install)

  ```console
  rvm --default use 3.0.0 
  ```
</details>

<details>
  <summary>Install Node</summary>

  [https://guides.rubyonrails.org/getting_started.html#installing-node-js-and-yarn](https://guides.rubyonrails.org/getting_started.html#installing-node-js-and-yarn)

  ```console
  npm -v
  ```
  
  ```console
  yarn -v
  ```
</details>

<details>
  <summary>Install Rails</summary>

  [https://guides.rubyonrails.org/getting_started.html#creating-a-new-rails-project-installing-rails-installing-rails]

  ```console
  gem install rails -v 7.0.0
  ```
  
  ```console
  rails -v
  ```
</details>

## Install Database
<details>
  <summary>Install Postgres</summary>

  [https://www.postgresql.org/download/macosx/](https://www.postgresql.org/download/macosx/)

  ```console
  psql --version
  ```
</details>

_-or-_

<details>
  <summary>Install SQLite3</summary>

  [https://guides.rubyonrails.org/getting_started.html#installing-sqlite3](https://guides.rubyonrails.org/getting_started.html#installing-sqlite3)
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

<details>
  <summary>Setup Shrine</summary>

  [Shrine](https://github.com/shrinerb/shrine) is a modular file upload toolkit that allows direct uploads to S3, resumable uploads, image processing and more.

  [This template](https://railsbytes.com/templates/xYasLK) installs Shrine gem, config initializer, plus adds some handy uploaders you can use.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/xYasLK'
  ```
</details>

## Project Configuration

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

