source "https://rubygems.org"

# Pin the whole dependency set to GitHub Pages' own gem so that a local
# `bundle exec jekyll serve` builds with the exact Jekyll version GitHub
# Pages runs on push. Do not add a standalone `gem "jekyll"` line — let
# github-pages choose the compatible version.
gem "github-pages", group: :jekyll_plugins

# Ruby 3.0+ dropped webrick from the standard library, and `jekyll serve`
# needs it for the local preview server.
gem "webrick"

# GitHub Pages pins an older Jekyll (3.9.x) that predates Ruby 3.4's removal
# of several libraries from the default gems. GitHub builds on Ruby 3.3, where
# these are still bundled, so this block does NOTHING there — it only kicks in
# for LOCAL builds on Ruby 3.4+ (e.g. Homebrew's current `ruby`) so that
# `bundle exec jekyll serve` still works. Prefer installing Ruby 3.3 locally to
# mirror GitHub exactly; these shims are a fallback for newer Rubies.
install_if -> { Gem::Version.new(RUBY_VERSION) >= Gem::Version.new("3.4") } do
  gem "csv"
  gem "base64"
  gem "bigdecimal"
  gem "logger"
end
