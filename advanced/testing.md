# Testing

> More to come!

Initialize the test database:

```sh
$ RAILS_ENV=test bundle exec rake db:schema:load db:seed cortex:core:db:reseed
$ RAILS_ENV=test bundle exec rake cortex:rebuild_indexes
```

To run Ruby and JS specs, utilize:

```sh
$ RAILS_ENV=test bundle exec rake spec
$ RAILS_ENV=test bundle exec rake spec:javascript
```
