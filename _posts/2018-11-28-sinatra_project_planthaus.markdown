---
layout: post
title:      "Sinatra Project: PLANTHAUS"
date:       2018-11-28 21:07:44 +0000
permalink:  sinatra_project_planthaus
---


My idea for this project is a simple CMS using Sinatra called PLANTHAUS which allows users to keep track of their houseplants. Each houseplant object contains information about name, type of plant, light and water requirements, purchase date, etc. The user will be able to add new plants, see an index of all their plants, and select each one to get more detailed information, edit that information, or delete plants. It proved to be an uphill battle that really reinforced my understanding of Sinatra's routes and ActiveRecord's handling of data. What follows are a few of my big a-ha moments along the way.

# Corneal
When I first started I began to create folders and files manually, modelled after previous labs and lessons but after attending a study group I learned of a Sinatra app generator called [Corneal ](https://thebrianemory.github.io/corneal/) which really simplified the whole app creation process. It included tools such as rspec and shotgun with some CSS to help spruce things up a bit visually. 

![file structure](https://i.imgur.com/D1lZRaG.png) 

What a great tool to get you going on a new Sinatra app! Now with my folder structure in place I could start building out my controllers, models, and views. I trimmed off some of the excess like the spec folder and logos but for the most part it was perfect out of the box.

# Uniqueness = ActiveRecord awesomeness
While working on the user validation part of my signup action I was beginning to get bogged down into a lot of logic in regards to the uniqueness of a username or email. I got the email working at first: 
```
if params[:email] == User.find_by(email: params[:email]).email
      flash[:errors] = "Could not create new account: There is already a user with that email address"
      redirect '/signup'
```
But when I tried to add the equivalent username check I kept getting errors. So rather than continue to bog my sellf down in what was beginning to smell like very un-DRY code I went to check if there was another way to separate that logic out. Another issue was that I had hard coded error messages for the uniqueness check but I was already using ActiveRecord errors to check when a field was left bank on sign up. And so I went off to Googleland and [lo and behold](https://guides.rubyonrails.org/active_record_validations.html#uniqueness) there was a validation helper similar to  *presence: true*  that could check for uniqueness and it is  *uniqueness: true* which would do that check for me in a very DRY and clean way. Now looking at my User model it is very readable and clear what its requirements for signup are. 
```
class User < ActiveRecord::Base
  has_secure_password
  validates :username, presence: true
  validates :username, uniqueness: true
  validates :email, presence: true
  validates :email, uniqueness: true

  has_many :plants
end
```

# rake db:rollback vs. add_column_to_a_table Migration
While working through some of the lessons leading up to this Sinatra project it took me a second to wrap my head around ActiveRecord migrations. One of the first and most useful commands was  ``rake db:migrate create_migration NAME=____ ``  to create a migration file where you could create your table in order to store your Object's attributes using ActiveRecord. Thanks to section leader Howard he reminded me of ``rake -T`` to display the available rake db commands, one of which was ``rake db:rollback``. But I don't think I paid much attention to what the actual application of that command was.

![rake commands](https://i.imgur.com/vCDn7XZ.png)

Well as I had already built out my Plant object that had its attributes in the migration file *create_plants* that included only name and plant_type. I went to code the display of these attributes in my show.erb file and of course added  some more details like water_requirements, light_requirements, and notes. Along with that I updated my create_table block in the *create_plants* migration file to include *t.string :water_requirement*  and such. But when I went to visit my show page, I kept getting errors like: 

![ERROR](https://i.imgur.com/HFHc9Vq.png)

Like what do you mean 'no method error'? I thought I defined that attribute! So after much anguish and misdirected aggression at the computer it turned out that I didn't really update the my Plants table by simply updating the migration file. I had to rollback and migrate again in order to recreate that table with the added colums of water_requirement, notes, etc. AHA! Alas all was back to normal. BUT WAS IT?! WHERE ARE MY PLANT INSTANCES THAT I CREATED BEFORE?! Well it turns out that when I rolled back my migration I actually dropped the whole Plants table with along with my all Plant object data stored in those rows. Of course that was dummy data but it was still a shock that drove home an important lesson on database migrations: **If you want to preserve the data in the table do not rollback and drop that table. Rather, create a new migration file and migrate it to make changes to an existing table**

Create new migration:
```
rake db:create_migration NAME=add_columns_to_plants_table
```
Then in the new migration file I'll add my colums:
```
class AddColumnsToPlantsTable < ActiveRecord::Migration
  def change
    add_column :plants, :water_requirement, :string
    add_column :plants, :light_requirement, :string
  end
end
```
Don't forget to migrate!
```
rake db:migrate
```

And with those insights I was able to build on my undestanding through this project. Like the first project I learned a lot more than I initially did when working through some of the lessons and even after I submitted my project. And as I submit this project I am excited for the project review and refactoring that will challenge my knowledge and probably raise some concerns that I have overlooked. I know I'll come out the other side even better. Come on, Flatiron, FLY ME TO THE MOON! LET ME PLAY AMONG THE STARS!

![SINATRA](https://i.ytimg.com/vi/pazWbj81QAM/hqdefault.jpg)





