# Decoro

Decorators for Rails. Use only certain code for views? Decorators are the spot to put it!

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'decoro'
```

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install decoro

## Usage

Say you have a need to transform products to an options array (for use in a select):

```ruby
class ProductsDecorator < ApplicationDecorator
  def options_for_select
    model.map { |p| [p.display_name, p.id] }
  end
end
```

Then in your view:

```ruby
- decorate(@products) do |products|
  = f.association :product, collection: products.options_for_select
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/decoro. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [code of conduct](https://github.com/[USERNAME]/decoro/blob/master/CODE_OF_CONDUCT.md).


## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Decoro project's codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/[USERNAME]/decoro/blob/master/CODE_OF_CONDUCT.md).
