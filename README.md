# Solidus Globalize

[![Build Status](https://travis-ci.org/spree-contrib/spree_globalize.svg?branch=master)](https://travis-ci.org/spree-contrib/spree_globalize)
[![Code Climate](https://codeclimate.com/github/spree-contrib/spree_globalize/badges/gpa.svg)](https://codeclimate.com/github/spree-contrib/spree_globalize)

This is the globalization project extracted from `solidus_i18n` for [Solidus.io][1] version 3.1+.

For previous Solidus versions you can just use [solidus_i18n][2].

See the [official Internationalization documentation][2] for more details.

Happy translating!

---

## Installation

Add the following to your `Gemfile`:

```ruby
gem 'solidus_globalize', github: 'solidusio-contrib/solidus_globalize', branch: 'master'
```

Run `bundle install`

You can use the generator to install migrations and append solidus_globalize assets to
your app spree manifest file.

    rails g spree:globalize:install

This will insert these lines into your spree manifest files:

```
vendor/assets/javascripts/spree/backend/all.js
//= require spree/backend/spree_globalize

vendor/assets/javascripts/spree/frontend/all.js
//= require spree/frontend/spree_globalize

vendor/assets/stylesheets/spree/frontend/all.css
*= require spree/frontend/spree_globalize
```

---

## Model Translations

This feature uses the [Globalize][3] gem to localize model data.
So far the following models are translatable:

    Product, Promotion, OptionType, Taxonomy, Taxon, Property and ShippingMethod.

Start your server and you should see a TRANSLATIONS link or a flag icon on each
admin section that supports this feature.

There are two configs that allow users to customize which locales
should be displayed as options on the translation forms and which should be
listed to customers on the frontend. You can set them on an initializer. e.g.

```ruby
SpreeI18n::Config.available_locales = [:en, :es, :'pt-BR'] # displayed on frontend select box
SpreeGlobalize::Config.supported_locales = [:en, :'pt-BR'] # displayed on translation forms
```

NOTE for early adopters: `Spree::Globalize` namespace is now `SpreeGlobalize`

PS. Please use symbols, not strings. e.g. `:'pt-BR'` not just `'pt-BR'`. Otherwise
you may get unexpected errors

Or if you prefer they're also available on the admin UI general settings section.

*Every record needs to have a translation. If by any chance you remove `solidus_globalize`
from your Gemfile, add some records and then add `solidus_globalize` gem back you might get
errors like ``undefined method for nilClass`` because Globalize will try fetch
translations that do not exist.*

---

## Contributing

[See corresponding guidelines][7]

---

Copyright (c) 2010-2015 [Spree Commerce Inc.][1] and other [contributors][5]. released under the [New BSD License][6]

[1]: https://solidus.io
[2]: http://guides.spreecommerce.com/developer/i18n.html
[3]: https://github.com/globalize/globalize
[5]: https://github.com/spree-contrib/spree_globalize/graphs/contributors
[6]: https://github.com/spree-contrib/spree_globalize/blob/master/LICENSE.md
[7]: https://github.com/spree-contrib/spree_globalize/blob/master/CONTRIBUTING.md
[8]: https://github.com/spree-contrib/spree_i18n
