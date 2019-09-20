---
layout: post
title:  "Rails admin Setup"
categories: rails
---

### 1. gem file
  gem 'rails_admin', '~> 0.7.0'

### 2. install
  rails g rails_admin:install
  
### 3 .if rails_admin

  bundle exec rails generate paper_trail:install --with-changes --with-associations

#### 4. if WillPaginate
In your config/initializers/kaminari.rb,  


    if defined?(WillPaginate)
      module WillPaginate
        module ActiveRecord
          module RelationMethods
            def per(value = nil) per_page(value) end
            def total_count() count end
          end
        end
        module CollectionMethods
          alias_method :num_pages, :total_pages
        end
      end
    end

