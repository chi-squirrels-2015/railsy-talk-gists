# Serialize in ActiveRecord

===

As you've probably noticed, ActiveRecord gets even more powerful when we work in Rails.

Imagine you want to view the JSON version of some data on a page. To do this, you'd go into that page's controller and change the format output:

```
def show
	@article = Article.find(params[:id])
	respond_to do |format|
	format.html
	format.json { render json: @article }
	end
end

```

calling '.json' on that show page will render the json for the @article.

___

### But how can I further customize this output?

___


ActiveRecord serializers can help you customize this JSON output.

Using the serializer on the model will allow you to specify the attributes you would like to show up when the show.json page is rendered.

Step 1: Add 'active_model_serializer' gem to your gemfile.

Step 2: Run 'rails generate serializer article' to create a serialize file in the app/serialize

Step 3: Check out your cool new Serializer file:

```
class ArticleSerializer < ActiveModel::Serializer
	attributes :id
end

```

Step 4: Add cool stuff:

- add more attributes in the serializer class

- options: `root: false` removes the root node from the JSON output. Options can be passed in the same render JSON block or placed inside their own method(`default_serializer_options`)

- add attributes that aren't defined on the model(such as calling the url for that page). Then define a matching method in the serializer.

```
def url
	article_url(object)
end
```

- Use associations within the serializer to show what is associated with that model.

```
class ArticleSerializer < ActiveModel::Serializer
	attributes :id
	has_many :tags
end
```

This can be further customized if you opened up a tag serializer.


- Enable editing(conditionally) by overriding the attributes method and adding editing capabilities.

```
def attributes
	info = super
	info[:edit_url] = edit_article_url(object)
	info
end
```


Then lets add some admin validations. But how do we access current_user if it is outside of the controller and view layers?
- The serializer has a built-in object called `scope` that is set to the current_user. We can then call admin on the scope.

```
info[:edit_url] = edit_article_url(object) if scope.admin?
```



