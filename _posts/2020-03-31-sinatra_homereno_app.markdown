---
layout: post
title:      "Sinatra HomeReno App"
date:       2020-03-31 23:12:15 -0400
permalink:  sinatra_homereno_app
---


This module was a challenging one for me. Before I started at Flatiron, I had plans to move my family accross the country and that definitely took a toll on my Sinatra assignments—but once the we settled into our new city, my focus was catch up. So here's what I learned...

Working with databases in Sinatra is seamless when compared to working with raw SQL queries (I don't like writing SQL). In order to get Sinatra working with your app's database, you'll need to include a few gems:

```
gem 'activerecord', '5.2'
gem 'sinatra-activerecord'
gem 'rake'
```

ActiveRecord will map your models with your database, taking care of ORM for you. And the Sinatra-ActiveRecord  gem will add some helpful rake tasks, making managing databases a breeze.

For example, in the SQL section of the Flatiron curriculum, there were some tedious labs where we would need to write out every migration in different files. We would start with out something like:

```
CREATE TABLE users (
     id INTEGER PRIMARY KEY,
     email TEXT,
		 passwrod TEXT
);
```

and then populate your table...

```
INSERT INTO  users (email, password) VALUES ('john@email.com, 'pretendthisisahashedpassword');
```

Ok that's enough. Here's how Sinatra-ActiveRecord saves you time. In. your terminal, just type in:

```
rake db:create_migration NAME=create_users
```

That's it! A migration has been created. Now create your table and the run `rake db:migrate`. Making relationships between models is a breeze with ActiveRecord. For example, in my app, my users has many relationship. To create this relationship, all I needed to do was add the following to my user and taks model.

```
class User < ActiveRecord::Base

     has_many :tasks

end


class Task < ActiveRecord::Base

     belongs_to :user

end
```

Done. The classes now share a has-many/belong-to relationship. Overall I appreciate the abstraction that Sinatra-ActiveRecord brings to an app. It just makes it faster to a Ruby app up and running.
