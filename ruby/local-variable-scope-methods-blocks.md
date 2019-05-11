# Which Scope for Local Variables in Methods or Blocks?

## Method definition

With method definitions, the local variable's scope is restricted to the method definition itself.

This means that:
* local variables initiated outside the method definition are not visible inside the method definition

```ruby
a = 7

def my_value(a)
  a += 10
end

my_value(a)
puts a

# => 7
```

* local variables initiated inside the method definition are [unavailable anywhere else](variables-initialized-inside-method-unavailable-elsewhere.md)

```ruby
a = 7

def my_def
  b = 5
end

c = a + b
puts c

# => undefined local variable or method `b' for main:Object
```

## Method invocation with a block

In case of a method with a block, the scoping rules differ from the rules for method definition.
A method invocation with a block has more open scoping rules: *the block can use and modify local variables that are defined outside the block.*

```ruby
a = 7
array = [1, 2, 3]

array.each do |element|
  a = element
end

puts a

# => 3
```
---
TIL #9 - 11/05/2019
