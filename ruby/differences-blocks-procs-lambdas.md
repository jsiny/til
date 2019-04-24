# Blocks, Procs, Lambdas: Many Similarities, Some Differences

## What are blocks?

A block is a piece of code that can be passed to an object or method and is executed under the context of that object.

It is defined between `{}` or between `do` and `end`. 

In Ruby, every method can accept one block as an argument. The block will be called thanks to the `yield` keyword.

```ruby
def congratulations(name)
  yield name if block_given?
end

congratulations("Hélène") { |name| puts "Wow that's incredible, #{name}!" }
# ==> Wow that's incredible, Hélène!
```


## What are procs?

A proc is an object from the Proc class. 

It is defined using `Proc.new` or `proc + <block>`.
