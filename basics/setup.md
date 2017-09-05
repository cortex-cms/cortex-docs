# Setup

> Note: Docker Compose instructions coming soon

### Environment

Copy and rename the example `.env.example` file as `.env` and modify it to match your environment.

For a rudimentary setup, these variables should be configured:

* Execute `$ bundle exec rails secret` twice to generate both an `APP_SECRET` and `DEVISE_SECRET`
* If the superuser isn't used for the app databases, the `DATABASE_USERNAME` and `DATABASE_PASSWORD` should be set accordingly.

### Dependencies

#### System

##### OS X

* Install the Xcode Command Line tools:

```sh
$ xcode-select --install
```

* Install all Cortex system-wide dependencies \(and the `readline` Ruby/`byebug` build dependency\) using [Homebrew](http://brew.sh/) from the `Brewfile` via `$ brew install $(cat Brewfile|grep -v "#")`
* Install Ruby via [rbenv](https://github.com/sstephenson/rbenv) or [rvm](https://rvm.io/).
* Enable system agents:

```sh
$ ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
$ ln -sfv /usr/local/opt/elasticsearch/*.plist ~/Library/LaunchAgents
$ ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
```

and start them with `brew services`:

```sh
$ brew services start postgresql
$ brew services start elasticsearch
$ brew services start redis
```

or `launchctl`:

```sh
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.elasticsearch.plist
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

##### Linux

* Install all Cortex system-wide dependencies \(and the `readline` Ruby/`byebug` build dependency\) using your distribution's package manager \(`pacman`, `apt-get`, `yum`, etc\). For example, with Ubuntu's `apt-get`:

```sh
$ apt-get install libreadline6-dev postgresql postgresql-contrib redis-server openjdk-8-jre imagemagick jpegoptim ghostscript
```

Ubuntu and Redhat/Fedora do not have an official `elasticsearch` package - you must use Elasticsearch's [repository](https://www.elastic.co/blog/apt-and-yum-repositories) or follow these [instructions](https://github.com/elastic/elasticsearch#installation). The same goes for `phantomjs`. Build from [source](http://phantomjs.org/download.html) or use a [PPA](https://launchpad.net/ubuntu/+ppas?name_filter=phantomjs). Other Linux distributions likely have these as prebuilt packages in their official or user repositories.

* Install Ruby via [rbenv](https://github.com/sstephenson/rbenv) or [rvm](https://rvm.io/).
* Enable system agents using your distribution's service manager frontend, which is likely `systemd`'s frontend, `systemctl`:

```sh
$ systemctl enable postgresql
$ systemctl enable elasticsearch
$ systemctl enable redis
```

and start them with `systemctl`:

```sh
$ systemctl start postgresql
$ systemctl start elasticsearch
$ systemctl start redis
```

#### Application

* Install Bundler and its dependencies:

```sh
$ gem install bundler && bundle install
```

* Install `node` dependencies \(including `bower`\) and use `bower-rails`'s rake task to install dependencies:

```sh
$ npm install && bundle exec rake bower:install:development
```

### Database

* Create databases:

```sh
$ bundle exec rake db:create
```

* Initialize the schema:

```sh
$ bundle exec rake db:schema:load
```

* Seed database with a top-level tenant, the superuser and Custom Content data, then rebuild the ElasticSearch index:

```sh
$ bundle exec rake db:seed
$ bundle exec rake cortex:core:db:reseed
$ bundle exec rake cortex:rebuild_indexes
```

### Server

Start Cortex, Sidekiq and live rebuild of Webpack scripts via Foreman:

```sh
$ foreman start -f Procfile.dev
```

The admin interface should now be accessible locally on port `3000`. To access Cortex as superadmin, login as `admin@cortexcms.org` with password `welcome1`.

