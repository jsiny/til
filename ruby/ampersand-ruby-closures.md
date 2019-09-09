# The `&` (ampersand) in Ruby closures

This might come as a surprise, but the following Ruby program
is absolutely correct:

```ruby
def first_method(&block)
  second_method(block)
end

def second_method(block)
  third_method(&block)
end

def third_method(&block)
  block.call
end

first_method { puts "hello!" }
# "hello!"
```

How come this `&` sign pops up and disappears in a seemingly random fashion?

If you're a bit confused about the various uses of the `&` sign in the 
context of closures (in particular, blocks and Procs), then you can read 
[my article](https://jsinibardy.com/ampersand-ruby-closures)
on the topic.

---
TIL #15 - 09/09/2019