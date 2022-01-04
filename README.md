# Rails Blueprint
> A starter blueprint for fast tracking Rails development

## Setup Environment
<details>
  <summary>Install Ruby</summary>

  [https://guides.rubyonrails.org/getting_started.html#installing-ruby](https://guides.rubyonrails.org/getting_started.html#installing-ruby)
  ```
  ruby -v 
  ```
</details>

<details>
  <summary>Install RVM</summary>

  [https://rvm.io/rvm/install](https://rvm.io/rvm/install)
  ```
  rvm --default use 3.0.0 
  ```
</details>

<details>
  <summary>Install Node</summary>

  [https://guides.rubyonrails.org/getting_started.html#installing-node-js-and-yarn](https://guides.rubyonrails.org/getting_started.html#installing-node-js-and-yarn)
  ```
  npm -v
  ```
  ```
  yarn -v
  ```
</details>

<details>
  <summary>Install Rails</summary>

  [https://guides.rubyonrails.org/getting_started.html#creating-a-new-rails-project-installing-rails-installing-rails]
  ```
  gem install rails -v 7.0.0
  ```
  ```
  rails -v
  ```
</details>

## Install Database
<details>
  <summary>Install Postgres</summary>

  [https://www.postgresql.org/download/macosx/](https://www.postgresql.org/download/macosx/)
  ```
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

  ```
rails new APP_NAME -s --git --database=postgresql --css=bootstrap --javascript=esbuild
  ```
</details>

-or-

<details>
  <summary>Stimulus + Postgres + Bootstrap + Webpack</summary>

  ```
rails new APP_NAME -s --git --database=postgresql --css=tailwind --javascript=webpack
  ```
</details>

-or-

<details>
  <summary>Stimulus + Postgres + Bootstrap + Rollup</summary>

  ```
rails new APP_NAME -s --git --database=postgresql --css=tailwind --javascript=rollup
  ```
</details>

## Migrate Database

```
rails db:create
rails db:migrate
```