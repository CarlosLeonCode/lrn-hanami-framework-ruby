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
% bundle exec hanami db prhttps://guides.hanamirb.org/v1.3/introduction/getting-started/the routes is a class specification, this isn't like RoR usage.
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
> | If you’re confused by ‘action’ vs. ‘controller’: Hanami only has action classes, so a controller is just a module to group several related actions together.

### Repositories and entities

We need a way to read and write to our database. There are two types of objects that we’ll use for this:

- An entity is a domain object (a Book) that is uniquely identified by its identity,
- A repository is what we use to persist, retrieve, and delete data for an entity, in the persistence layer.
- Entities are entirely unaware of the database. This makes them lightweight and easy to test.
- Since entities are completely decoupled from the database, we use repositories to persist the data
- An entity is something really close to a plain Ruby object.
- The repository is also the place where you would define new methods to implement custom queries.

#### Entities
An entity is something really close to a plain Ruby object. We use them to model the behavior we want from a concept (a book, in this case)

##### Code example of Repositories usage

```ruby
$ bundle exec hanami console
>> repository = BookRepository.new
  # => #<BookRepository relations=[:books]>
>> repository.all
  # => []
>> book = repository.create(title: 'TDD', author: 'Kent Beck')
  # => #<Book:0x007f9ab61c23b8 @attributes={:id=>1, :title=>"TDD", :author=>"Kent Beck", :created_at=>2018-10-24 11:11:38 UTC, :updated_at=>2018-10-24 11:11:38 UTC}>
>> repository.find(book.id)
  # => #<Book:0x007f9ab6181610 @attributes={:id=>1, :title=>"TDD", :author=>"Kent Beck", :created_at=>2018-10-24 11:11:38 UTC, :updated_at=>2018-10-24 11:11:38 UTC}>
```
### Expose method on Actions

By using the expose method in our action class, we can expose the contents of our @books instance variable to the outside world, so that Hanami can pass it to the view. That’s enough to make all our tests pass again!
