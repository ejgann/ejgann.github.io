---
layout: post
title:      "The Enchantment of Rails' Nested Attributes"
date:       2020-04-01 12:54:29 -0400
permalink:  the_enchantment_of_rails_nested_attributes
---


If Rails' nested attributes was a toy featured in a toy store's front window, I would totally be the kid with her nose pressed to the glass, staring in awe at its beauty and coolness.

Nested attributes are an incredibly efficient Rails feature that enables you to save attributes on associated records through its parent model. 

Let's say that you are creating an app to track the dogs in a dog shelter, and part of the information you want to store includes the toys that each dog likes to play with. To start breaking this down, let's look at the nested hash of a newly created instance of a dog model and its params:

```
{"dog"=> {
	"name"=>"Molly",
	"toys"=>[
		{
			"toy_name"=>"Squeaky ball",
			"colors"=>"Red/Blue",
			"characteristics"=>"When dropped, it bounces"
		}, {
			"toy_name"=>"Stuffed dinosaur",
			"colors"=>"Purple",
			"characteristics"=>"A plush toy that makes a noise when squeezed"
}, {
			"toy_name"=>"Frisbee",
			"colors"=>"Green/Orange",
			"characteristics"=>"When thrown, it flies"
}}]}}
```

If we needed to create a new instance of dog in the app, we would fill out a form (as part of the controller's create action) that would look like this:

```
<%= form_for @dog do |t| %>
		<%= f.label :name %>
		<%= f.text_field :name %>
	
		<%= f.fields_for :toys do |toy| %>
				<%= toy.label :toy_name %>
				<%= toy.text_field :toy_name %>
				
				<%= toy.label :colors %>
				<%= toy.text_field :colors %>
		
				<%= toy.label :characteristics %>
				<%= toy.text_area :characteristics %>

		<% end %>
<%= f.submit %>
<% end %>
```

This form, and more specifically the iterative `fields_for` helper method, allows the user to add as many toys per newly created dog as the user needs. But, how do those multiple toys, which "belongs_to" a dog, get created for that particular instance of dog? This leads us to consider the second part of this Rails feature.

The `fields_for` feature alone will not create the relationship between each dog toy and its associated dog in our app's database. We must also switch to the model file to add another key component — `accepts_nested_attributes_for`.

```
class Dog < ActiveRecord::Base
		has_many :toys
		accepts_nested_attributes_for :toys
end
```

The line `accepts_nested_attributes_for :toys` plus the `fields_for` code from before are what successfully create any new toys added and associated with a new instance of a dog. In other words, you need to have these lines of code in order to link the added toys to the dog model. The `accepts_nested_attributes_for` line of code creates an attribute writer method in the dog model,  `toy_attributes=(attributes)` , which is what allows the user to add toys to the dog instance.

Now, if we go back to the nested hash showing the code added for Molly and her favorite toys, we see what exactly happened after we added these two lines of code:

```
{"dog"=> {
	"name"=>"Molly",
	"toys_attributes"=> {
			"0"=> {
					"toy_name"=>"Squeaky ball",
					"colors"=>"Red/Blue",
					"characteristics"=>"When dropped, it bounces"
				}, 
			"1"=> {
					"toy_name"=>"Stuffed dinosaur",
					"colors"=>"Purple",
					"characteristics"=>"A plush toy that makes a noise when squeezed"
		}, 
			"2"=> {
					"toy_name"=>"Frisbee",
					"colors"=>"Green/Orange",
					"characteristics"=>"When thrown, it flies"
}}}},

"commit"=>"Create Dog", "controller"=>"dogs", "action"=>"create"}
```

We now have a new key within our nested hash called "toys_attributes", and each subsequently listed toy now has a unique params key through which it can be identified in the params hash and associated with its parent model, dog. 

Rails never ceases to amaze me, and the nested attributes feature is only the most recent example of that. I hope you have a new appreciation for this feature, too. Happy coding!

