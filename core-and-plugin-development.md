# Core & Plugin Development

## Local Development Setup

First, clone the necessary repositories:

```bash
$ git clone git@github.com:cortex-cms/cortex-starter.git
$ git clone git@github.com:cortex-cms/cortex.git
$ git clone git@github.com:cortex-cms/cortex-plugins-core.git
$ git clone your-plugin-repo-here.git
```

Use `pwd` to retrieve the fully qualified path for each engine, then modify each of the following files to point to the relevant local dependencies:

* `cortex/Gemfile`
* `cortex/spec/dummy/package.json`
* `cortex-starter/Gemfile`
* `cortex-starter/package.json`

For example:

{% code-tabs %}
{% code-tabs-item title="cortex-starter/Gemfile" %}
```ruby
# Cortex
gem 'cortex', path: '/home/testuser/repos/cortex'
gem 'cortex-plugins-core', path: '/home/testuser/repos/cortex-plugins-core'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="cortex-starter/package.json" %}
```javascript
"cortex": "/home/testuser/repos/cortex",
"cortex-plugins-core": "/home/testuser/repos/cortex-plugins-core"
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Lastly, re-install dependencies in the relevant projects.

## Running Test Suite

Initialize the test database:

```bash
$ RAILS_ENV=test bundle exec rake db:schema:load db:seed cortex:core:db:reseed
$ RAILS_ENV=test bundle exec rake cortex:rebuild_indexes
```

To run Ruby and JS specs, utilize:

```bash
$ RAILS_ENV=test bundle exec rake spec
$ RAILS_ENV=test bundle exec rake spec:javascript
```



