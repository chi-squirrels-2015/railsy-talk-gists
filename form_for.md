Using 'form_for' is a lot like form_tag, only it does more for you. 

In sinatra, you would have had to type something like this for the first line of a form: 

```html

<form action='/users' method='POST'>

```

In rails, this line is replaced with:

```ruby

<% form_for(@user) do |f| %> 

```

Form_for checks for a @user object and will handle the routing for that object.

The next part of the form is the input. In sinatra, it would have looked something like this:


```html

 <label for="name">Name</label>
 <input id="user" type="text" name="user[name]">


```

In rails, that code is replaced with:

```ruby

		  <%= f.label :name %>
		  <%= f.text_field :name %>

```
Using f in the iteration ties the form to user, which is the same as doing "user[name]" in sinatra. 

If the object exists, it will fill in the values for the form and will handle the method accordingly. If there is not an @user object, the form will be blank. You can add placeholders or classes to your forms if want, much in the same way you would have in sinatra.


```ruby

<%= f.text_field :name, class: "col-md-4 control-label", placeholder: "Enter Your Name" %>

```

The last part of the form is the submit button. 

In sinatra, we would use:

```html

<input type="submit" value="Submit">


```
In rails, this is replaced with

```ruby

<%= f.submit %>

```

Because Rails automatically checks the @user object to see if it exists, the default button in this case would say "Create User". If it already exists, the button would by default say "Update User". If you don't like the way this sounds, you can override the button. 

```ruby

<%= f.submit  "Make Yo Account!" %>

```


The final form would look like this:

```ruby

		<%= form_for(@user) do |f| %>
		  <%= f.label :first_name %>
		  <%= f.text_field :first_name %>

		  <%= f.label :last_name %>
		  <%= f.text_field :last_name %>

		  <%= f.label :email %>
		  <%= f.text_field :email%>

		  <%= f.label :password %>
		  <%= f.password_field :password %>

		  <%= f.submit %>
		<% end %>

```
