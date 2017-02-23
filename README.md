# Redis Puppet Module for Boxen

[![Build Status](https://travis-ci.org/boxen/puppet-redis.png?branch=master)](https://travis-ci.org/boxen/puppet-redis)

## Fork
We forked `boxen/puppet-redis` because we need to use a specific version of redis (the one in puppet-redis 3.1.0), but that version uses the oudated `sha1` directive in its brewfile.
This fork updates 3.1.0 to use the `sha256` directive. To pull it into your boxen repo, put the following in your boxen Puppetfile:
```
github "redis", "3.1.1", repo: "dobtco/puppet-redis"`
```

## Usage

```puppet
include redis
```

## Required Puppet Modules

* boxen
* homebrew
* stdlib

### Environment

Once installed, you can access the following variables in your environment, projects, etc:

* BOXEN_REDIS_PORT: the configured redis port
* BOXEN_REDIS_URL: the URL for redis, including localhost & port

#### Hubot

For [hubot](https://github.com/github/hubot) development, particularly using the [redis-brain](https://github.com/github/hubot-scripts/blob/master/src/scripts/redis-brain.coffee), you'll need the following:

```shell
export REDISTOGO_URL=$BOXEN_REDIS_URL
```

#### Ruby

```ruby
$redis = Redis.new(:host => '127.0.0.1', :port => ENV['BOXEN_REDIS_PORT'] || '6379'
```
