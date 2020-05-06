# Photo App

# Build Authentication System

1. **Add the following in Gemfile**
> gem 'devise'  
> gem 'twitter-bootstrap-rails'  
> gem 'devise-bootstrap-views'
2. Install gem in cmd:  
   - `rails g devise:install`  
   - `rails g devise User`
3. Open devise_create_users migration file and uncomment under _##Confirmable_
4. Open user.rb model file and add ***:confirmable,*** after _:registerable_
5. `rails db:migrate`
6. Add the following in application_controller.rb
```
protect_from_forgery with: :exception  
before_action :authenticate_user!
```
7. Add the following after class definition
> skip_before_action :authenticate_user!, only: [:index]  
_Normally the root route will direct to login page, but after putting this line it will stay in localhost:3000_
8. run in cmd
- `rails g bootstrap:install static` 
- `rails g bootstrap:layout application`
- `rails g devise:views:locale en`
- `rails g devise:views:bootstrap_templates`
9. Remove five fevicon tags in application.html.erb
10. Add `gem 'jquery-rails'` in Gemfile and bundle install
11. Add `//= link application.js` in app\assets\config\manifest.js
12. Add `config.action_mailer.defaut_url_options = { :host => 'http://localhost:3000' }` in config\environments\development.rb
13. For Image Upload
> gem 'carrierwave'
> gem 'mini_magick'
> gem 'fog'
14. `rails g scaffold Image name:string picture:string user:references` and rails db:migrate