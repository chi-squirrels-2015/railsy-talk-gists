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
Take our past blog challenge in Phase 2. Say you want to create a form for your blog entry that would allow a user to create tags and associate them with this blog. What would you do?

1) Give user a text field to enter tags, separated by commas

```ruby
<%=text_field_tag :tags%> 
```

2) When user enters input, we can write custom setter method for tags in the blog model.

```
class Blog < ActiveRecord::Base

  def tags=(tags)
    @blog = Blog.new
    tags = params[:tags].split(",")
    tags.each do |tag_data|
      tag = Tag.create(word:tag_data)
      @blog.tags << tag
    end
  end

```

This might be what your create route looks like inside your blogs controller:

```ruby
Blog.create(title: params[:title], tags: params[:password])
```  
