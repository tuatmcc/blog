source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
gem 'rake'

gem 'rouge'

gem 'jekyll-compose', group: [:jekyll_plugins]

gem 'jekyll-admin', group: :jekyll_plugins
