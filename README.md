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
  <summary>Stimulus + Postgres + Bootstrap + Esbuild</summary>

  ```console
  rails new . -s --git --database=postgresql --css=bootstrap --javascript=esbuild
  ```
</details>

_-or-_

<details>
  <summary>Stimulus + Postgres + Bootstrap + Webpack</summary>

  ```console
  rails new . -s --git --database=postgresql --css=tailwind --javascript=webpack
  ```
</details>

_-or-_

<details>
  <summary>Stimulus + Postgres + Bootstrap + Rollup</summary>

  ```console
  rails new . -s --git --database=postgresql --css=tailwind --javascript=rollup
  ```
</details>

## Migrate Database

```console
rails db:create
rails db:migrate
```

## User Authentication

<details>
  <summary>Setup Devise</summary>

  [Devise](https://github.com/heartcombo/devise) is flexible authentication solution for Rails with Warden.

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

  ```console
  rails app:template LOCATION='https://railsbytes.com/templates/z0gsEQ'
  ```

  Learning More:
  - [Migrate Models](https://github.com/jhawthorn/discard#usage)
  - [Discard Record](https://github.com/jhawthorn/discard#discard-a-record)
  - [Undiscard Record](https://github.com/jhawthorn/discard#undiscard-a-record)
  - [Default Scopes](https://github.com/jhawthorn/discard#default-scope)
</details>