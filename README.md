# Lrn Hanami Framework Ruby

Welcome to your new Hanami project!

## Setup

How to run tests:

```
% bundle exec rake
```

How to run the development console:

```
% bundle exec hanami console
```

How to run the development server:

```
% bundle exec hanami server
```

How to prepare (create and migrate) DB for `development` and `test` environments:

```
% bundle exec hanami db prepare

% HANAMI_ENV=test bundle exec hanami db prepare
```

Explore Hanami [guides](https://guides.hanamirb.org/), [API docs](http://docs.hanamirb.org/1.3.5/), or jump in [chat](http://chat.hanamirb.org) for help. Enjoy! 🌸


# Concepts

Our project can have many applications on it. All of them inside the app folder.
Every action specified in the routes is a class specification, this isn't like RoR usage.
The view is a ruby class.

```ruby
# Route definition
root to: 'home#index'

# Controller definition
module Web
  module Controllers
    module Home
      class Index
        include Web::Action
        # some code
      end
    end
  end
end

# View definition - this is .rb file
module Web
  module Views
    module Home
      class Index
        include Web::View
        # some code
      end
    end
  end
end

# ! The real view is defined inside templates folder
# templates/home/index.html.erb
```
