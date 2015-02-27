## session

Sessions are used in applications to pass and persist data while a user is logged in, and session data is only available in the controller and the view. All sessions store their data in cookies, and this comes with a lot of great functionality: cookies are lightweight, come built-into the server, and also provide encryption. As a result, sending data through sessions is more secure way than sending data than through the URL.

It's important to note that cookies can only store a limited amount of data (about 4kB), which is why storing large amounts of data in sessions is discouraged. Sessions should only be used to store critical data or data that will be used for long periods of time.

## flash

The flash provides a way to pass temporary primitive-types (String, Array, Hash) between actions. The flash works just like a session in that it carries information to another action. However, anything you place in the flash will be exposed to the very next action and then cleared out. This is a great way of passing notices and alerts.


```ruby
class LoginController < ActionController::Base
  def destroy
    session[:user_id] = nil
    flash[:notice] = “You have successfully logged out.”
    redirect_to root_url
  end

end
```

```html
<!-- logout.html.erb -->

<% if flash[:notice] %>
  <div class=“notice”><%= flash[:notice] %></div>
<% end %>
```