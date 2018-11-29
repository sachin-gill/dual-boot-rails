source 'https://rubygems.org'

module Bundler::SharedHelpers
  def default_lockfile=(path)
    @default_lockfile = path
  end

  def default_lockfile
    @default_lockfile ||= Pathname.new("#{default_gemfile}.lock")
  end
end

module ::Kernel
  def rails_next?
    ENV["RAILS_NEXT"] == '1'
  end
end

if rails_next?
  Bundler::SharedHelpers.default_lockfile =
    Pathname.new("#{Bundler::SharedHelpers.default_gemfile}_next.lock")

  class Bundler::Dsl
    unless method_defined?(:to_definition_unpatched)
      alias_method :to_definition_unpatched, 
        :to_definition
    end

    def to_definition(_bad_lockfile, unlock)
      to_definition_unpatched(Bundler::SharedHelpers.default_lockfile, unlock)
    end
  end
end

if rails_next?
  gem 'rails', '4.2.0'
else 
  gem 'rails', '3.2.2'
end 

# Bundle edge Rails instead:
# gem 'rails', :git => 'git://github.com/rails/rails.git'

gem 'sqlite3'


# Gems used only for assets and not required
# in production environments by default.
group :assets do
  if !rails_next?
    gem 'sass-rails',   '~> 3.2.3'
    gem 'coffee-rails', '~> 3.2.1'

    # See https://github.com/sstephenson/execjs#readme for more supported runtimes
    # gem 'therubyracer'

    gem 'uglifier', '>= 1.0.3'
  end
end

gem 'jquery-rails'

# To use ActiveModel has_secure_password
# gem 'bcrypt-ruby', '~> 3.0.0'

# To use Jbuilder templates for JSON
# gem 'jbuilder'

# Use unicorn as the app server
# gem 'unicorn'

# Deploy with Capistrano
# gem 'capistrano'

# To use debugger
# gem 'ruby-debug19', :require => 'ruby-debug'
