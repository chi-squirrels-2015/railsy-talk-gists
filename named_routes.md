## named_routes (:as)

So let's say we have controller called photos_controllers.rb. We want to know what the routes should be. Yeah? So we're going to use ~~scaffolding~~ resources in our config/routes.rb file to have all of our routes mapped for us.

```ruby
resources :photos
```

| HTTP Verb  | Path | Controller#Action | Used for |
| ------------- | ------------- | ------------- | ------------- |
| GET | /photos  | photos#index  | display a list of all photos  |
| GET | /photos/new  | photos#new  | return an HTML form for creating a new photo  |
| POST | /photos  | photos#create  | create a new photo  |
| GET | /photos/:id  | photos#show  | display a specific photo  |
| GET | /photos/:id/edit  | photos#edit  | return an HTML form for editing a photo  |
| PATCH/PUT | /photos/:id  | photos#update  | update a specifc photo  |
| DELETE | /photos/:id  | photos#destroy  | delete a specific photo  |

Awesome, looks really similar to the routes that we are all familiar with so far. But hold on, we also have a sessions_controller.rb and a users_controller.rb which will deal with signup, login, and logout. So in our routes, we will also have this:

```ruby
get    'signup', to: 'users#new' 
get    'login',  to: 'sessions#new'
post   'login',  to: 'sessions#create'
delete 'logout', to: 'sessions#destroy'

resources :photos
```

Now we are going to have something that looks like this:

| Prefix | HTTP Verb  | Path | Controller#Action | Used for |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| user | GET | /signup  | users#new  |  |
| login | GET | /login  | sessions#new  |  |
|  | POST | /login  | sessions#create  |  |
| logout | DELETE | /logout | sessions#destroy | | 
| photos | GET | /photos  | photos#index  | display a list of all photos  |
| new_photo | GET | /photos/new  | photos#new  | return an HTML form for creating a new photo  |
| | POST | /photos  | photos#create  | create a new photo  |
| | GET | /photos/:id  | photos#show  | display a specific photo  |
| edit_photo | GET | /photos/:id/edit  | photos#edit  | return an HTML form for editing a photo  |
| | PATCH/PUT | /photos/:id  | photos#update  | update a specifc photo  |
| | DELETE | /photos/:id  | photos#destroy  | delete a specific photo  |

Alright, getting a little crazy, but nothing we shouldn't be able to handle. So let's get into what we're talking about today, which is naming the routes by using :as.

So let's say instead of using "photos" in our prefixes, we want to have them switched for "pictures". Check it, all we have to do is add an `as: :pictures` right after we do `resources :photos`. Let's see how that looks in the routes.rb file.

```ruby
get    'signup', to: 'users#new' 
get    'login',  to: 'sessions#new'
post   'login',  to: 'sessions#create'
delete 'logout', to: 'sessions#destroy'

resources :photos, as: :pictures
```

Sweet, let's see what that looks!

| Prefix | HTTP Verb  | Path | Controller#Action | Used for |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| user | GET | /signup  | users#new  |  |
| login | GET | /login  | sessions#new  |  |
|  | POST | /login  | sessions#create  |  |
| logout | DELETE | /logout | sessions#destroy | | 
| pictures | GET | /photos  | photos#index  | display a list of all photos  |
| new_picture | GET | /photos/new  | photos#new  | return an HTML form for creating a new photo  |
| | POST | /photos  | photos#create  | create a new photo  |
| | GET | /photos/:id  | photos#show  | display a specific photo  |
| edit_pictures | GET | /photos/:id/edit  | photos#edit  | return an HTML form for editing a photo  |
| | PATCH/PUT | /photos/:id  | photos#update  | update a specifc photo  |
| | DELETE | /photos/:id  | photos#destroy  | delete a specific photo  |

Looks great. And we can even do this to custom routes, like we made for the signup, login, and logout. This is how it's going to look if we want to change up the logout:

```ruby
get    'signup', to: 'users#new'
get    'login',  to: 'sessions#new'
post   'login',  to: 'sessions#create'
delete 'logout', to: 'sessions#destroy', as: :signout

resources :photos, as: :pictures
```

Guess on what it's going to do?

| Prefix | HTTP Verb  | Path | Controller#Action | Used for |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| user | GET | /signup  | users#new  |  |
| login | GET | /login  | sessions#new  |  |
|  | POST | /login  | sessions#create  |  |
| signout | DELETE | /logout | sessions#destroy | | 
| pictures | GET | /photos  | photos#index  | display a list of all photos  |
| new_picture | GET | /photos/new  | photos#new  | return an HTML form for creating a new photo  |
| | POST | /photos  | photos#create  | create a new photo  |
| | GET | /photos/:id  | photos#show  | display a specific photo  |
| edit_pictures | GET | /photos/:id/edit  | photos#edit  | return an HTML form for editing a photo  |
| | PATCH/PUT | /photos/:id  | photos#update  | update a specifc photo  |
| | DELETE | /photos/:id  | photos#destroy  | delete a specific photo  |

All done! The `as:` can also be used for nested routes as well. Feel free to experiment doing this by running `rake routes` in your command line after you mess with your routes to really see what is going on. Have fun!