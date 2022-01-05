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
-or-
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

-or-

<details>
  <summary>Stimulus + Postgres + Bootstrap + Webpack</summary>

  ```console
rails new . -s --git --database=postgresql --css=tailwind --javascript=webpack
  ```
</details>

-or-

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
- What attributes? `name`

Post Installation Steps:
1. In `config/environments/development.rb`, add `config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }`
2. Copy Devise views
```console
rails g devise:views
```
3. Migrate Database:
```console
rails db:migrate
```
</details>