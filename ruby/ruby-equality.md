# Making sense of Equality in Ruby

How come there are so many `=` signs in Ruby programs?

Here's a short program:

```ruby
def some_method(a)
  if a == 5
    a = 3
  elsif (1..10) === a
    a += 10
  else
    [1, 2, 3][2] = 4
  end
end

p some_method(5)  # => 3
p some_method(2)  # => 12
p some_method(15) # => 4
```

In the above code, we have no less than 5 different forms of `=`:
* `=` in `a = 3`
* `+=` in `a += 10`
* `[]=` in `[1, 2, 3][2] = 4`
* `==` in `if a == 5`
* `===` in `elsif (1..10) === a`

If you want to know more about this `=` madness, check out 
[my blog post](https://jsinibardy.com/ruby-equality)
on the matter.

---
TIL #14 - 05/08/2019