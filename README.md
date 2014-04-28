## bundle dependency resolution gotcha

I'm having trouble resolving dependencies with a version constraint "~> 0".

See [bundler #3001](https://github.com/bundler/bundler/issues/3001).

Gem `a` depends on `rack ~> 0`, which should match any rack version.

Gem `b` depends on `rack 1.4.5`.

I'd expect version rack 1.4.5 to satisfy both constraints.

Running `bundle install` (v1.6.2) gives an error.

```
$ bundle install
Resolving dependencies...
Bundler can't satisfy your Gemfile's dependencies.
Install missing gems with `bundle install`.
Fetching source index from https://rubygems.org/
Resolving dependencies...
Bundler could not find compatible versions for gem "rack":
  In Gemfile:
    a (>= 0) ruby depends on
      rack (~> 0) ruby

    b (>= 0) ruby depends on
      rack (1.4.5)

$ bundle --version
Bundler version 1.6.2
```
