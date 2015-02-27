##Shoulda Matchers
Create a series of shorthands for otherwise much more complicated and long winded rspec tests for rails

###Setup
Include the Gem in your Gemfile
```ruby
group :test do
  gem 'shoulda-matchers', require: false
end
```

Then require the gem following rspec-rails in your rails_helper/ spec_helper
```ruby
require 'rspec/rails'
require 'shoulda/matchers'
```


##Shamelessly Stolen, Useful Links
### ActiveModel Matchers

* **[allow_mass_assignment_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/allow_mass_assignment_of_matcher.rb)**
  tests usage of Rails 3's `attr_accessible` and `attr_protected` macros.
* **[allow_value](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/allow_value_matcher.rb)**
  tests usage of the `validates_format_of` validation.
* **[have_secure_password](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/have_secure_password_matcher.rb)**
  tests usage of `has_secure_password`.
* **[validate_confirmation_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/validate_confirmation_of_matcher.rb)**
  tests usage of `validates_confirmation_of`.
* **[validate_exclusion_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/shoulda/matchers/active_model/validate_exclusion_of_matcher.rb)**
  tests usage of `validates_exclusion_of`.
* **[validate_inclusion_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/validate_inclusion_of_matcher.rb)**
  tests usage of `validates_inclusion_of`.
* **[validate_length_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/validate_length_of_matcher.rb)**
  tests usage of `validates_length_of`.
* **[validate_numericality_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/validate_numericality_of_matcher.rb)**
  tests usage of `validates_numericality_of`.
* **[validate_presence_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_model/validate_presence_of_matcher.rb)**
  tests usage of `validates_presence_of`.

### ActiveRecord Matchers

* **[accept_nested_attributes_for](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/accept_nested_attributes_for_matcher.rb)**
  tests usage of the `accepts_nested_attributes_for` macro.
* **[belong_to](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/association_matcher.rb)**
  tests your `belongs_to` associations.
* **[define_enum_for](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/define_enum_for_matcher.rb)**
  tests usage of the `enum` macro.
* **[have_and_belong_to_many](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/association_matcher.rb)**
  tests your `has_and_belongs_to_many` associations.
* **[have_db_column](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/have_db_column_matcher.rb)**
  tests that the table that backs your model has a specific column.
* **[have_db_index](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/have_db_index_matcher.rb)**
  tests that the table that backs your model has an index on a specific column.
* **[have_many](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/association_matcher.rb)**
  tests your `has_many` associations.
* **[have_one](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/association_matcher.rb)**
  tests your `has_one` associations.
* **[have_readonly_attribute](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/have_readonly_attribute_matcher.rb)**
  tests usage of the `attr_readonly` macro.
* **[serialize](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/serialize_matcher.rb)** tests
  usage of the `serialize` macro.
* **[validate_uniqueness_of](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/active_record/validate_uniqueness_of_matcher.rb)**
  tests usage of `validates_uniqueness_of`.

### ActionController Matchers

* **[filter_param](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/filter_param_matcher.rb)**
  tests parameter filtering configuration.
* **[redirect_to](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/redirect_to_matcher.rb)**
  tests that an action redirects to a certain location.
* **[render_template](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/render_template_matcher.rb)**
  tests that an action renders a template.
* **[render_with_layout](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/render_with_layout_matcher.rb)**
  tests that an action is rendered with a certain layout.
* **[rescue_from](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/rescue_from_matcher.rb)**
  tests usage of the `rescue_from` macro.
* **[respond_with](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/respond_with_matcher.rb)**
  tests that an action responds with a certain status code.
* **[route](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/route_matcher.rb)** tests
  your routes.
* **[set_session](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/set_session_matcher.rb)**
  makes assertions on the `session` hash.
* **[set_flash](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/set_flash_matcher.rb)**
  makes assertions on the `flash` hash.
* **[use_after_action](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/use_after_action.rb)**
  tests that a `after_action` callback is defined in your controller. (Aliased
  as *use_after_filter*.)
* **[use_around_action](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/use_around_action.rb)**
  tests that a `around_action` callback is defined in your controller. (Aliased
  as *use_around_filter*.)
* **[use_before_action](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/action_controller/use_before_action.rb)**
  tests that a `before_action` callback is defined in your controller. (Aliased
  as *use_before_filter*.)

### Independent Matchers

* **[delegate_method](https://github.com/thoughtbot/shoulda-matchers/blob/master/lib/shoulda/matchers/independent/delegate_method_matcher.rb)**
  tests that an object forwards messages to other, internal objects by way of
  delegation.
