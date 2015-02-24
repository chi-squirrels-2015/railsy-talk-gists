## virtual-attributes
We are used to having models with attributes that match table columns. However, there is a way to get around this! We introduce to you virtual attributes!! 
A couple of examples:

This is what the Users table looks like. 
```ruby
 
  create_table :users do |t|
    t.string :first_name
    t.string :last_name
    t.string :password
    end
```

This is the original form with first name and last name.
```ruby
<h1>Register</h1>
  <% form_for :user, :url => users_path do |f| %>
  <p>
    First Name<br />
    <%= f.text_field :first_name %>
  </p>
  <p>
    Last Name <br />
    <%= f.text_field :last_name %>
  </p>
  <p>
    Password<br/>
    <%= f.password_field :password %>
  </p>
  <p>
    <%= submit_tag 'Register' %>
  </p>
  <% end %>
 ```
 But! What if you wanted to refer to the user with their full name instead?
 ```ruby 
<h1>Register</h1>
  <% form_for :user, :url => users_path do |f| %>
  <p>
    Full Name<br />
    <%= f.text_field :full_name %>
  </p>
  <p>
    Password<br/>
    <%= f.password_field :password %>
  </p>
  <p>
    <%= submit_tag 'Register' %>
  </p>
  <% end %>
```

In order to do this, custom setter and getter methods need to be created:
```ruby
Model:
class User < ActiveRecord::Base
  def full_name
    [first_name, last_name].join(' ')
  end

  def full_name=(name)
    split = name.split(' ',2)
    self.first_name = split.first
    self.last_name = split.last
  end
end
```
This is what you might find in the create route that this form is set to.
```ruby
User.create(fullname: params[:fullname], password: params[:password])  
```                                           
