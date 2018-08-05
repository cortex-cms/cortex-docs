# Manual

## `cortex-starter` Prep

As `cortex` itself is only a Rails Engine, it needs to be mounted within a parent Rails applicaton. [cortex-starter](https://github.com/cortex-cms/cortex-starter) serves as a starting point for new users, with `cortex` and `cortex-plugins-core` already mounted and configured with several example `ContentTypes`/`Decorators`. Start by cloning the repository:

```bash
git clone git@github.com:cortex-cms/cortex-starter.git && cd cortex-starter
```

## Environment

Copy and rename the example `.env.example` file as `.env` and modify it to match your environment.

For a rudimentary setup, these variables should be configured:

* Execute `$ bin/rails secret` twice to generate both an `APP_SECRET` and `DEVISE_SECRET`
* If the superuser isn't used for the app databases, the `DATABASE_USERNAME` and `DATABASE_PASSWORD` should be set accordingly.

## Dependencies

### System

#### OS X

* Install the Xcode Command Line tools:

```bash
$ xcode-select --install
```

* Install all Cortex system-wide dependencies \(and the `readline` Ruby/`byebug` build dependency\) using [Homebrew](http://brew.sh/) from the `Brewfile` via `$ brew install $(cat Brewfile|grep -v "#")`
* Install Ruby via [rbenv](https://github.com/sstephenson/rbenv) or [rvm](https://rvm.io/).
* Enable system agents:

```bash
$ ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
$ ln -sfv /usr/local/opt/elasticsearch/*.plist ~/Library/LaunchAgents
$ ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
```

and start them with `brew services`:

```bash
$ brew services start postgresql
$ brew services start elasticsearch
$ brew services start redis
```

or `launchctl`:

```bash
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.elasticsearch.plist
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

#### Linux

* Install all Cortex system-wide dependencies \(and the `readline` Ruby/`byebug` build dependency\) using your distribution's package manager \(`pacman`, `apt-get`, `yum`, etc\). For example, with Ubuntu's `apt-get`:

```bash
$ apt-get install libreadline6-dev postgresql postgresql-contrib redis-server openjdk-8-jre imagemagick jpegoptim ghostscript
```

Ubuntu and Redhat/Fedora do not have an official `elasticsearch` package - you must use Elasticsearch's repositories for [APT](https://www.elastic.co/guide/en/elasticsearch/reference/current/deb.html) or [RPM](https://www.elastic.co/guide/en/elasticsearch/reference/current/rpm.html) or follow these [manual instructions](https://www.elastic.co/guide/en/elasticsearch/reference/current/_installation.html). The same goes for `phantomjs`. Build from [source](http://phantomjs.org/download.html) or use a [PPA](https://launchpad.net/ubuntu/+ppas?name_filter=phantomjs). Other Linux distributions likely have these as prebuilt packages in their official or user repositories.

* Install Ruby via [rbenv](https://github.com/sstephenson/rbenv) or [rvm](https://rvm.io/).
* Enable & start system agents using your distribution's service manager frontend, which is likely `systemd`'s frontend, `systemctl`:

```bash
$ systemctl enable --now postgresql elasticsearch redis
```

### Application

* Install Bundler and its dependencies:

```bash
$ gem install bundler && bundle install
```

* Install `node` dependencies using `yarn`:

```bash
$ yarn install
```

## Database

* Create databases:

```bash
$ bin/rails db:create
```

* Initialize the schema:

```bash
$ bin/rails db:schema:load
```

* Seed database with a top-level tenant, the superuser and Custom Content data, then rebuild the ElasticSearch index:

```bash
$ bin/rails db:seed
$ bin/rails cortex:core:db:reseed
$ bin/rails cortex:rebuild_indexes
```

## Server

Start Cortex, Sidekiq and live rebuild of Webpack scripts via Foreman:

```bash
$ foreman start -f Procfile.dev
```

The admin interface should now be accessible locally on port `3000`. To access Cortex as superadmin, login as `admin@cortexcms.org` with password `welcome1`.

