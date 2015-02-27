### SimpleForm
SimpleForm takes those nasty forms we have been writing and *simplifies* them. 

## Basic Setup

# Add it to your Gemfile:

`gem 'simple_form'`

# Run the following command to install it:

`bundle install`

# Run the generator:

`rails generate simple_form:install`

# If using Bootstrap, run this generator instead:

`rails generate simple_form:install --bootstrap`

[SimpleForm documentation](https://github.com/plataformatec/simple_form)

The code below should look familiar:

```ruby
<%= form_for @question do |f| %>  
  <%= f.error_messages %>
  <p>  
    <%= f.label :title %>  
    <%= f.text_field :title %>  
  </p>
  <p>  
    <%= f.label :category_id %>  
    <%= f.collection_select :category_id, Category.all, :id, :name %>  
  </p>
  <p>  
    <%= f.label :content %>  
    <%= f.text_field :content %>  
  </p>  
  <p><%= f.submit %></p>  
<% end %>
```

The code below should look a little more pleasant:

```ruby
<%= simple_form_for @question do |f| %>
  <%= f.error_messages %>
  <%= f.input :title %>
  <%= f.association :category %> 
  <%= f.input :content %>
  <%= f.button :submit %>
<% end %>
```

The key differences between normal forms in Rails vs. SimpleForm:
- form_for is replaced with simple_form_for.
- Most of the time, labels and inputs are replaced with SimpleForm's f.input method.
- f.collection_select is replaced with the f.assocations method. 

A reminder on why this last point is so great:
```ruby
  <p>  
    <%= f.label :category_id %>  
    <%= f.collection_select :category_id, Category.all, :id, :name %>  
  </p>
```
  
### VS.

```ruby
  <%= f.association :category %> 
```

F.collection select indeed.


