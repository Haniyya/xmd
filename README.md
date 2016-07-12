# Xmd
## XML Mapping DSL

This gem defines an xml mapping dsl to parse xml-nodes.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'xmd'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install xmd

## Usage

```ruby
class Parser
  include Xmd::DSL

  node message: :description
  nodes items: :item do
    node external_url: :link
    attribute :published, class: :date

    nodes dates: :date do
      note :beginning, class: :date
      note :end, class: :date
    end
  end
end

feed = open url do |xml|
  Parser.parse xml
end

feed.message #=> 'A description'
item = feed.items.first
item.external_url #=> The entries Link

```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/xmd. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

