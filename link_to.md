link_to(name, url, options &block)
===

##name - the actual text that will appear as the link

It can be a literal string, or a method that returns a string, like an active record method call on an object

##options 

**:back** - directs the route back to the referring page
```
<%= link_to "Go Back", :back %>
```
**method:** _*:verb*_ - defines a method other than POST or GET with a symbol :put, :patch, :delete
```
<%= link_to profile.name, profile_path(profile), method: :delete %>
```
**remote:** _*true*_ - allows for AJAX request, instead of following the link route
```
<%= link_to profile.name, remote: true %>
```
**target:** _* "_blank"*_ - creates a popup window
```
<%= link_to profile.popup, profile_popup_path, target: "_blank" %>
```
**data:** used to add custom data attributes

**confirm:** _*'Are you sure?'*_ (Alert window with OK/Cancel)
```
<%= link_to profile.name, profile_path(profile), method: :delete, data: { confirm: 'Are you sure?' %> }
```
**:disable_with** - disables the link, for JavaScript
```
<%= link_to profile.name, data: :disable_with %>
```                 
**class:** _*'class-name'*_
**id:** _*'id-name'*_
**&block** - can be used if the name is complicated and cannot be easily fit into the name parameter
```
<%= link_to(@profile) do %>
    <strong><%= @profile.name %></strong> -- <span>Check it out!</span>
          <% end %>
```
*that is this:*
```
<a href="/profiles/1"><strong>David</strong> -- <span>Check it out!</span></a>
```
**:pop-up**
```
link_to name, url, :popup => ['dialog name', 'toolbar=no, location=no, directories=no, status=no, menubar=no, scrollbars=yes, resizable=yes']
```

##Actual Ruby Code
```
module ActionView
  module Helpers
    module UrlHelper
      def link_to(*args, &block)
        if block_given?
          options = args.first || {}
          html_options = args[1]
          concat(link_to(capture(&block), options, html_options))
        else
          name = args.first
          options = args[1] || {}
          html_options = args[2]
          url = case options
            when String
              options
            when :back
              @controller.request.env["HTTP_REFERER"] || 'javascript:history.back()'
            else
              self.url_for(options)
            end

          if html_options
            html_options = html_options.stringify_keys
            href = html_options['href']
            convert_options_to_javascript!(html_options, url)
            tag_options = tag_options(html_options)
          else
            tag_options = nil
          end

          href_attr = "href=\"#{url}\"" unless href
          "<a #{href_attr}#{tag_options}>#{name || url}</a>"
        end
      end
    end
  end
end
```
Other Variations
===============
link_to_if (condition, name, url, options)

link_to_unless (condition, name, url, options)

link_to_if_current (name, url, options)
