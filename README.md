# Rails Blueprint
A [starter blueprint](https://dev.to/dalezak/a-starter-blueprint-to-help-fast-track-a-new-rails-applications-4671) to help fast track setting up a new Rails application.

## Getting Started
To get started, choose one of the following options. 

<details>
  <summary>Clone Repo</summary>

  Replace `my_app` with the name of your application.
  ```clone
  git clone https://github.com/dalezak/rails-blueprint.git my_app
  ```
</details>

_-or-_

<details>
  <summary>Download Repo</summary>

  Download and extract [https://github.com/dalezak/rails-blueprint/archive/refs/heads/main.zip](https://github.com/dalezak/rails-blueprint/archive/refs/heads/main.zip) into folder with the name of your application.
</details>

_-or-_

<details>
  <summary>Follow Online</summary>

  Instead of cloning or downloading the repo, you can also just follow these [steps online](https://github.com/dalezak/rails-blueprint/blob/main/README.md).
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

  Add the following section to your `package.json`:
  ```javascript
  "scripts": { 
    "build:css": "sass ./app/assets/stylesheets/application.bootstrap.scss ./app/assets/builds/application.css --no-source-map --load-path=node_modules" 
  }
  ```
</details>

_-or-_

<details>
  <summary>Postgres + Tailwind + Esbuild</summary>

  Creates a new Rails project with Postgres database, Tailwind css and ESbuild javascript.
  ```console
  rails new . -s --git --database=postgresql --css=tailwind --javascript=esbuild
  ```

  Add the following section to your `package.json`:
  ```javascript
  "scripts": { 
    "build:css": "sass ./app/assets/stylesheets/application.bootstrap.scss ./app/assets/builds/application.css --no-source-map --load-path=node_modules" 
  }
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
  <summary>Postgres + Tailwind + Webpack</summary>

  Creates a new Rails project with Postgres database, Tailwind css and Webpack javascript.
  ```console
  rails new . -s --git --database=postgresql --css=tailwind --javascript=webpack
  ```
</details>

_-or-_

<details>
  <summary>Postgres + Bootstrap + Rollup</summary>

  Creates a new Rails project with Postgres database, Bootstrap css and Rollup javascript.
  ```console
  rails new . -s --git --database=postgresql --css=bootstrap --javascript=rollup
  ```
</details>

_-or-_

<details>
  <summary>Postgres + Tailwind + Rollup</summary>

  Creates a new Rails project with Postgres database, Tailwind css and Rollup javascript.
  ```console
  rails new . -s --git --database=postgresql --css=tailwind --javascript=rollup
  ```
</details>

## Migrate Database
After creating your Rails project, you'll need to run `rails db:create` to create the local database.

## UUID Keys

<details>
  <summary>Enable UUIDs</summary>

  Use UUIDs as the default primary key for your models.

  [This template](https://railsbytes.com/public/templates/V4Ys1d) enables pgcrypto for UUIDs.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/V4Ys1d'
  ```
</details>

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
  - What attributes? `name` _# use space separated list of attributes_

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

  For more a advanced use of CanCanCan, read [Lazy Load CanCanCan Abilities In Rails](https://dev.to/dalezak/lazy-load-cancancan-abilities-in-rails-1h10).

  Learning More:
  - [Defining Abilities](https://github.com/CanCanCommunity/cancancan#define-abilities)
  - [Checking Abilities](https://github.com/CanCanCommunity/cancancan#check-abilities)
  - [Controller Helpers](https://github.com/CanCanCommunity/cancancan#controller-helpers)
  - [Developer Guide](https://github.com/CanCanCommunity/cancancan/blob/develop/docs/README.md)
  - [GoRails Tutorial](https://gorails.com/episodes/authorization-with-cancancan)
</details>

_-or-_

<details>
  <summary>Setup Pundit</summary>

  [Pundit](https://github.com/varvet/pundit) provides a set of helpers which guide you in leveraging regular Ruby classes and object oriented design patterns to build a simple, robust and scalable authorization system.

  [This template](https://railsbytes.com/templates/X6ks6o) installs the Pundit gem, and runs the generator.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/X6ks6o'
  ```
</details>

## User Invitations
Options for allowing ability to invite users if you're using [Devise](https://github.com/heartcombo/devise).

<details>
  <summary>Setup Devise Inviteable</summary>

  [devise_invitable](https://github.com/scambra/devise_invitable) is an invitation strategy for Devise.

  [This template](https://railsbytes.com/templates/VZgsJ0) installs the gem, and runs the generator.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/VZgsJ0'
  ```
</details>

## Single Sign On
Allows users the ability to login to your application through other services like Google.

<details>
  <summary>Setup Omniauth</summary>

  [Omniauth](https://github.com/omniauth/omniauth) is a flexible authentication system utilizing Rack middleware. 

  [This template](https://railsbytes.com/templates/xkjsK3) adds Omniauth gem, adds OmniauthController, adds Identity model, runs migrations
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/xkjsK3'
  ```

  Post Installation Steps:
  1. Add or update routes in  `config/routes.rb` to include `omniauth_callbacks`
  ```console
  devise_for :users, controllers: { omniauth_callbacks: "omniauth" }
  ```

  Learning More:
  - [Getting Started](https://github.com/omniauth/omniauth/wiki#getting-started)
  - [GoRails Tutorial](https://gorails.com/episodes/omniauth-twitter-sign-in)
</details>

<details>
  <summary>Add Omniauth Google Provider</summary>

  [omniauth-google-oauth2](https://github.com/zquestz/omniauth-google-oauth2) is oauth2 strategy for Google.

  [This template](https://railsbytes.com/templates/V4YsP6) adds the gem, omniauth provider, runs migration on users.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/V4YsP6'
  ```
</details>

<details>
  <summary>Add Omniauth Github Provider</summary>

  [omniauth-github](https://github.com/omniauth/omniauth-github) is oauth2 strategy for Github.

  [This template](https://railsbytes.com/templates/Vwysyy) adds the gem, omniauth provider, runs migration on users.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/Vwysyy'
  ```
</details>

<details>
  <summary>Add Omniauth Twitter Provider</summary>

  [omniauth-twitter](https://github.com/arunagw/omniauth-twitter) is oauth2 strategy for Twitter.

  [This template](https://railsbytes.com/templates/XE5sQy) adds the gem, omniauth provider, runs migration on users.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/XE5sQy'
  ```
</details>

<details>
  <summary>Add Omniauth Facebook Provider</summary>

  [omniauth-facebook](https://github.com/simi/omniauth-facebook) is oauth2 strategy for Facebook.

  [This template](https://railsbytes.com/templates/zyvsjm) adds the gem, omniauth provider, runs migration on users.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/zyvsjm'
  ```
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
Add file upload functionality to a cloud storage services.

<details>
  <summary>Setup ActiveStorage</summary>

  [ActiveStorage](https://edgeguides.rubyonrails.org/active_storage_overview.html) facilitates uploading files to a cloud storage service like Amazon S3, Google Cloud Storage, or Microsoft Azure.

  [This template](https://railsbytes.com/templates/zJosLx) adds ActiveStorage to your Rails app.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/zJosLx'
  ```
</details>

_-or-_

<details>
  <summary>Setup Shrine</summary>

  [Shrine](https://github.com/shrinerb/shrine) is a modular file upload toolkit that allows direct uploads to Amazon S3, resumable uploads, image processing and more.

  [This template](https://railsbytes.com/templates/xYasLK) installs Shrine gem, config initializer, plus adds some handy uploaders you can use.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/xYasLK'
  ```
</details>

## App Analytics

<details>
  <summary>Setup Ahoy</summary>

  [Ahoy](https://github.com/ankane/ahoy) is simple, powerful, first-party analytics for Rails.

  [This template](https://railsbytes.com/templates/V1bs4X) adds Ahoy gem, runs its initializer and then migrates the database.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/V1bs4X'
  ```
</details>

## Accept Payments

<details>
  <summary>Setup Pay</summary>

  [Pay](https://github.com/pay-rails/pay) add payments using Stripe or Braintree to your application.

  [This template](https://railsbytes.com/templates/zPdsZn) adds gem and runs generators.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/zPdsZn'
  ```
</details>

## Error Reporting

<details>
  <summary>Setup Sentry</summary>

  [Sentry](https://sentry.io) is error tracking to performance monitoring, developers can see what actually matters, solve quicker, and learn continuously about their applications - from the frontend to the backend.

  [This template](https://railsbytes.com/templates/zOvsol) adds gem, initializer and application controller code.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/zOvsol'
  ```
</details>

_-or-_

<details>
  <summary>Setup HoneyBadger</summary>

  [HoneyBadger](https://www.honeybadger.io/for/rails/) lets you track and debug exceptions in record time. 

  [This template](https://railsbytes.com/templates/zNPsmV) adds gem, sets api key runs initializer.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/zNPsmV'
  ```
</details>

## Bootstrap Styling

<details>
  <summary>Bootstrap Navbar & Layout</summary>

  Add a Bootstrap 5 navbar and page layout, plus bunch of partials and helpers.

  [This template](https://railsbytes.com/templates/zmnsEn) updates the layout with navbar.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/zmnsEn'
  ```
</details>

## Project Configuration
Some handy project configurations to make your life simpler.

<details>
  <summary>Open Browser After Launch</summary>

  This snippet will automatically open your Rails app in the browser after launch.

  [This template](https://railsbytes.com/templates/zl0s3A) adds snippet to `config.ru`.
  ```console
  rails app:template LOCATION="https://railsbytes.com/script/zl0s3A"
  ```
</details>

<details>
  <summary>Setup Bullet</summary>

  [Bullet](https://github.com/flyerhzm/bullet) helps kill N+1 queries and unused eager loading.

  [This template](https://railsbytes.com/templates/XLEsaW) adds gem and initializer.
  ```console
  rails app:template LOCATION="https://railsbytes.com/script/XLEsaW"
  ```
</details>

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
  <summary>Annotate Models</summary>

  [Annotate](https://github.com/ctran/annotate_models) provides classes with schema and routes info.

  [This template](https://railsbytes.com/templates/Vqqsqg) installs gem, and runs annotations.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/Vqqsqg'
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
  <summary>Access Rails Credentials Using ENV</summary>

  This [strategy](https://dev.to/dalezak/rails-environment-variables-using-credentials-mh7) adds a config initializer which lets you access your `Rails.application.credentials` using `ENV`.

  [This template](https://railsbytes.com/templates/Vp7s90) adds a config initializer.
  ```console
  rails app:template LOCATION='https://railsbytes.com/script/Vp7s90'
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

## Git Aliases
Some [handy git aliases](https://dev.to/dalezak/git-aliases-are-like-superpowers-3bp4) I like to use to save time.

<details>
  <summary>Git Add Commit Push</summary>

  This alias does a git add, commit and push all on one line. 

  ```console
  git config --global alias.add-commit-push '!git add -A && git commit -m "$1" && git push && git status'
  ```

  You can use the `add-commit-push` alias like this.
  ```console
  git add-commit-push "Add, commit, push in one line!"
  ```
</details>

<details>
  <summary>Git New Branch</summary>

  This alias adds, commits and pushes current changes to a new branch.

  ```console
  git config --global alias.new-branch '!git checkout -b "$1" && git add -A && git commit -m "$2" && git push -u origin "$1" && git status'
  ```

  You can use the `new-branch` alias like this.
  ```console
  git new-branch "123-my-branch" "Checkout, add, commit, push!"
  ```
</details>

<details>
  <summary>Git New Tag</summary>

  This alias creates a new tag and pushes it using the timestamp for naming.

  ```console
  git config --global alias.new-tag '!git tag -a -m `date +'%Y-%m-%d_%H-%M'` `date +'%Y-%m-%d_%H-%M'` && git push origin `date +'%Y-%m-%d_%H-%M'` && git status'
  ```

  You can use the `new-tag` alias like this.
  ```console
  git new-tag
  ```
</details>

## VS Code Extensions
Some handy extensions for [Visual Studio Code](https://code.visualstudio.com).

<details>
  <summary>Rails</summary>

  Ruby on Rails support for Visual Studio Code

  [https://marketplace.visualstudio.com/items?itemName=bung87.rails](https://marketplace.visualstudio.com/items?itemName=bung87.rails)
</details>

<details>
  <summary>Ruby</summary>

  This extension provides enhanced Ruby language and debugging support for Visual Studio Code

  [https://marketplace.visualstudio.com/items?itemName=rebornix.Ruby](https://marketplace.visualstudio.com/items?itemName=rebornix.Ruby)
</details>

<details>
  <summary>Ruby Language Colorization</summary>

  Ruby Language Colorization for Visual Studio Code

  [https://marketplace.visualstudio.com/items?itemName=groksrc.ruby](https://marketplace.visualstudio.com/items?itemName=groksrc.ruby)
</details>

<details>
  <summary>Ruby on Rails</summary>

  This extension for Visual Studio Code adds snippets for Ruby on rails.

  [https://marketplace.visualstudio.com/items?itemName=hridoy.rails-snippets](https://marketplace.visualstudio.com/items?itemName=hridoy.rails-snippets)
</details>

<details>
  <summary>Ruby Solargraph</summary>

  Solargraph is a language server that provides intellisense, code completion, and inline documentation for Ruby.

  [https://marketplace.visualstudio.com/items?itemName=castwide.solargraph](https://marketplace.visualstudio.com/items?itemName=castwide.solargraph)
</details>

<details>
  <summary>Simple Ruby ERB</summary>

  This extensions tries to provide simple Ruby and ERB support to Visual Studio Code without messing with linting or debugging.

  [https://marketplace.visualstudio.com/items?itemName=vortizhe.simple-ruby-erb](https://marketplace.visualstudio.com/items?itemName=vortizhe.simple-ruby-erb)
</details>

<details>
  <summary>VSCode Ruby</summary>

  This extension provides improved syntax highlighting, language configuration, and snippets to Ruby and ERB files within Visual Studio Code.

  [https://marketplace.visualstudio.com/items?itemName=wingrunr21.vscode-ruby](https://marketplace.visualstudio.com/items?itemName=wingrunr21.vscode-ruby)
</details>

<details>
  <summary>Ruby Rubocop</summary>

  This extension provides interfaces to rubocop for vscode.

  [https://marketplace.visualstudio.com/items?itemName=misogi.ruby-rubocop](https://marketplace.visualstudio.com/items?itemName=misogi.ruby-rubocop)
</details>

## Rails Templates
Visit [railsbytes.com](https://railsbytes.com/public/templates) for other handy templates to help setup your project.

## Rails Tutorials

If you are looking for Rails tutorials, I'd highly recommend you checkout [gorails.com](https://gorails.com) and [driftingruby.com](https://www.driftingruby.com), both great resources for learning Rails.
