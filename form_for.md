Using 'form_for' is a lot like form_tag, only it does more for you. 

The first part of creating a form is using form_for. In sinatra, you would have had to type something like this for the first line: 

<form action='/users' method='POST'>

In rails, this line is replaced with:

<% form_for(@users) do |f| %> 

Form_for checks the @users object and will handle the routing for that object.

The next part of the form is the input. In sinatra, it would have looked something like this:

 <label for="name">Name</label>
 <input id="user" type="text" name="user[name]">

In rails, that code is replaced with:

		  <%= f.label :name %>
		  <%= f.text_field :name %>

using f in the iteration ties the form to user, which is the same as doing "user[name]" in sinatra.

The last part of the form is the submit button. 

In sinatra, we would use:
<input type="submit" value="Submit">

In rails, this is replaced with

<%= f.submit %>

Rails automatically checks the @user object to see if it exists. If it doesn't, the default button would say "Create User". If it already exists, form_for fills in the existing information, and changes to update the object. The button also updates to "Update User". If you don't like the way this sounds, you can override the button. 

<%= f.submit  "Make Yo Account!" %>



The final form would look like this:

		<%= form_for(@user) do |f| %>
		  <%= f.label :first_name %>
		  <%= f.text_field :first_name %>

		  <%= f.label :last_name %>
		  <%= f.text_field :last_name %>

		  <%= f.label :email %>
		  <%= f.text_field :email%>

		  <%= f.label :password %>
		  <%= f.password_field :password %>

		  <%= f.submit  "Create Account" %>
		<% end %>
