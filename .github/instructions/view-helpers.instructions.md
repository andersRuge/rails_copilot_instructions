---
applyTo: "**/*.erb,**/*.rb,**/helpers/*.rb"
---
# Action View Helpers Guidelines

## Core Concepts
- Use Rails built-in helpers for common view tasks
- Keep helpers focused on presentation logic
- Create custom helpers in dedicated modules
- Follow semantic HTML principles
- Use appropriate helpers for security (sanitization)
- Consider performance implications with caching helpers

## Formatting Helpers
### Date and Time Formatting
- Use `distance_of_time_in_words` for human-readable time differences
- Prefer `time_ago_in_words` for displaying relative timestamps
- Use `Time.current` instead of `Time.now` to respect time zones
- Format dates consistently across the application

```ruby
# Preferred usage
distance_of_time_in_words(Time.current, order.created_at)
time_ago_in_words(article.published_at)
```

### Number Formatting
- Use `number_to_currency` for monetary values
- Use `number_to_percentage` for percentage values
- Use `number_to_human_size` for file sizes
- Use `number_with_delimiter` for large numbers
- Use `number_with_precision` for decimal formatting

```ruby
# Preferred usage
number_to_currency(product.price)
number_to_percentage(completion_rate, precision: 1)
number_to_human_size(file.size)
number_with_delimiter(large_number)
```

### Text Processing
- Use `truncate` for limiting text length with proper indicators
- Use `excerpt` to extract relevant portions of text
- Use `word_wrap` for formatting paragraphs
- Use `pluralize` for dynamic singular/plural text
- Use `simple_format` to convert newlines to HTML breaks

```ruby
# Preferred usage
truncate(article.body, length: 100)
excerpt(comment.body, search_term, radius: 20)
pluralize(count, "item")
```

## Navigation Helpers
- Use `link_to` with path helpers for consistent linking
- Use `button_to` for actions that change data
- Use `url_for` when dynamic URL generation is needed
- Use `current_page?` for conditional navigation highlighting
- Use `mail_to` for email links with proper formatting

```ruby
# Preferred usage
link_to "View Details", product_path(product), class: "link"
button_to "Delete", product_path(product), method: :delete, class: "btn-danger"
```

## Asset Helpers
- Use `image_tag` instead of HTML img tags
- Use `javascript_include_tag` for script inclusion
- Use `stylesheet_link_tag` for CSS files
- Use `audio_tag` and `video_tag` for media elements
- Leverage `asset_path` for asset URL generation

```ruby
# Preferred usage
image_tag "logo.svg", alt: "Company Logo", class: "header-logo"
stylesheet_link_tag "application", media: "all"
```

## Form Helpers
- Use `form_with` with model binding when possible
- Use appropriate field helpers (`text_field`, `select`, etc.)
- Implement proper error handling with `field_with_errors`
- Use `collection_select` for model associations
- Leverage form builders for consistent styling

```ruby
# Preferred usage
<%= form_with model: @article do |form| %>
  <%= form.text_field :title, class: "form-control" %>
  <%= form.collection_select :category_id, Category.all, :id, :name %>
<% end %>
```

## Security Helpers
- Use `sanitize` for user-generated HTML content
- Use `strip_tags` to remove all HTML from content
- Use `strip_links` to remove links but keep text
- Use `escape_javascript` for JavaScript content
- Use `html_escape` or the `h` alias for HTML escaping

```ruby
# Preferred usage
sanitize user_content, tags: %w(p strong em ul li)
escape_javascript(render partial: "comments/comment")
```

## Layout Helpers
- Use `capture` to store generated markup in variables
- Use `content_for` for defining regions in layouts
- Use `yield` to render content in layout regions
- Use `render` with proper partial references
- Use `tag` helper for building custom HTML elements

```ruby
# Preferred usage
<% content_for :sidebar do %>
  <%= render "shared/sidebar_content" %>
<% end %>

<%= tag.div id: "container", class: "main-content" do %>
  <%= yield %>
<% end %>
```

## Performance Optimization
- Use `cache` helper for fragment caching
- Use `benchmark` to identify slow rendering sections
- Cache expensive helper operations
- Use Russian Doll caching pattern for nested content
- Consider moving expensive operations to background jobs

```ruby
# Preferred usage
<% cache [product, current_pricing] do %>
  <%= render product %>
<% end %>

<% benchmark "Rendering complex component" do %>
  <%= render "complex_component" %>
<% end %>
```

## Custom Helper Organization
- Keep view helpers in dedicated modules
- Group helpers by functionality
- Create base helpers for shared functionality
- Use proper namespacing for specialized helpers
- Document complex helpers with comments

```ruby
# app/helpers/formatting_helper.rb
module FormattingHelper
  def format_status(status)
    tag.span class: "status-#{status.downcase}" do
      status.titleize
    end
  end
end
```

## Testing Helpers
- Write tests for complex custom helpers
- Test helpers with various input scenarios
- Mock complex dependencies in helper tests
- Test for proper HTML escaping
- Ensure helper performance is acceptable