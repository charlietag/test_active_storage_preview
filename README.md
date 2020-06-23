# README
* Try rails built-in packages
  * Active Storage
  * Preview
    * PDF
    * Video
    * Images

## Packages

* Ruby version
  * 2.7.0

* Rails version
  * 6.0.3.2

## Basic setup
* Gems - useful for dev
  * gem 'pry-rails', :group => :development
  * gem 'bullet', group: 'development'

	```bash
	# basic useful dev packages
	gem 'pry-rails', :group => :development
	gem 'bullet', group: 'development'
	```

* jQuery
  * yarn add jquery
    * test_active_storage_preview/app/javascript/packs/application.js

      ```bash
      import "jquery/src/jquery"
      ...
      ```

* bootstrap
  * yarn add bootstrap popper.js (don't add popper v2, bootstrap default requires v1.16) , (no need to import popper.js manually, bootstrap will do it automatically)
    * app/javascript/packs/application.js
      * `import "bootstrap/dist/js/bootstrap"`
    * app/assets/stylesheets/application.css
      * `*= require 'bootstrap/dist/css/bootstrap'`

## Rails setup

* generate scaffold
  * `bin/rails g scaffold Book name:string author:string`
  * `bin/rails g scaffold Movie name:string actor:string`
  * `bin/rails g scaffold Artist name:string age:integer`

* Install active_storage
  * `bin/rails active_storage:install`


## config - credential

* command
  * `EDITOR=vim bundle exec rails credentials:edit`

    ```bash
    development:
      db:
        user: user
        pass: pass

    production:
      db:
        user: user
        pass: pass
    ```

* config/database.yml

  ```bash
  default: &default
    adapter: mysql2
    encoding: utf8mb4
    pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
    username: <%= Rails.application.credentials[Rails.env.to_sym][:db][:user] %>
    password: <%= Rails.application.credentials[Rails.env.to_sym][:db][:pass] %>
    socket: /var/lib/mysql/mysql.sock

  development:
    <<: *default
    database: test_active_storage_preview_development

  test:
    <<: *default
    database: test_active_storage_preview_test

  production:
    <<: *default
    database: test_active_storage_preview_production
  ```

* Create database
  * `bundle exec rails db:create`

## Changes
* Basic config and setup
  * https://github.com/charlietag/test_active_storage_preview/compare/v0.0.0...v0.0.1
* Start to test active storage , preview pdf , images , videos
  * https://github.com/charlietag/test_active_storage_preview/compare/v0.0.1...master

## Final Result

![prview_images.png](/screenshots/preview_images.png)
![prview_pdf.png](/screenshots/preview_pdf.png)
![prview_video.png](/screenshots/preview_video.png)

## Note

* Internet media type (MIME)
  * `application/pdf`
  * `image/*`
  * `video/*`
* All MIME
  * [link](https://zh.wikipedia.org/zh-tw/%E4%BA%92%E8%81%94%E7%BD%91%E5%AA%92%E4%BD%93%E7%B1%BB%E5%9E%8B)
	* [link](https://blog.gtwang.org/web-development/html-input-accept-attribute-tutorial/)
