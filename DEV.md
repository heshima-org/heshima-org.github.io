# Getting started

## Testing the site locally

Install latest ruby, e.g. with <https://github.com/rbenv/rbenv>

    rbenv install -l
    rbenv install 3.1.2
    rbenv global 3.1.2

Install bundler <https://bundler.io/>, install bundles and start site locally

    bundle config set --local path ~/local/gem/heshima/bundle
    bundle install
    bundle exec jekyll serve
