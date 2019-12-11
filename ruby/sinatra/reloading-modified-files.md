# Reloading Modified Files in a Sinatra application

Killing and reloading the local webserver for each insignificant
change is both really painful and error-prone, as the following situation
will arise more than I care to admit:

> Why isn't it working? Shoot, I forgot to reload the server...

Fortunately, the useful [`Sinatra::Contrib` gem](http://sinatrarb.com/contrib/)
solves this problem through the
[`Sinatra::Reloader` extension](http://sinatrarb.com/contrib/reloader).

Simply add the following lines at the beginning of you Sinatra (classic)
application:

```ruby
# my_sinatra_app.rb

require 'sinatra'     # already here
require 'sinatra/reloader' if development?

require_relative 'other_important_file'

configure do
  also_reload 'other_important_file.rb' if development?
end
```

Notice that the `also_reload` statement requires the inclusion of the
extension (whereas the `require_relative` does not).

The `also_reload` statement doesn't have to be included in a `configure` block
if you're dealing with a Classic Application (and not a Modular Application),
but I think it looks cleaner this way.

To avoid repeating the `if development?` conditional, you can also group
these statements into their own `configure` block:

```ruby
configure(:development) do
  require 'sinatra/reloader'
  also_reload 'other_important_file.rb'
end
```

Now, any time you change something from `my_sinatra_app.rb` or
`other_important_file.rb`, the changes will directly appear on your localhost!

[More information in the documentation page](http://sinatrarb.com/contrib/reloader)

---
TIL #16 - 11/12/2019