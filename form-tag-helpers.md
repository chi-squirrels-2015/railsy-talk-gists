## form_tag helpers
The helper method form_tag takes a url/path, and an optional method (which is defaults to `post`). When method equals `patch`, `put`, or `delete` a hidden input tag is created with `name="_method"`. You must use form element `_tag` methods inside your `form_tag`.

*IMPORTANT: form_tag is not form_for!*

```ruby
<%= form_tag("/login", method: "post") %>
  <%= label_tag      :email                       %>
  <%= text_field_tag :email, nil, placeholder: "Email" %>

  <%= label_tag      :password, "Password:"                   %>
  <%= password_tag   :password, nil, placeholder: "Password" %>

  <%= submit_tag     "Login"   %>
<% end %>
```

```html
<form action="/login" method="POST">
  <label for="email">Email</label>
  <input type="text" id="email" name="email" placeholder="Email"/>
  <label for="password">Password:</label>
  <input type="password" id="password" name="password" placeholder="Password"/>
  <input name="commit" type="submit" value="Login" />
</form>
```