# Getting started

## Testing the site locally

Install latest ruby, e.g. with <https://github.com/rbenv/rbenv>

    rbenv install -l
    rbenv install 3.2.1
    rbenv global 3.2.1

Install bundler <https://bundler.io/>, install bundles and start site locally

    bundle config set --local path ~/local/gem/heshima/bundle
    bundle install
    bundle exec jekyll serve
