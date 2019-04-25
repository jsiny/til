# Blocks, Procs, Lambdas: Many Similarities, Some Differences

## Introduction

Blocks, procs and lambdas are examples of **closures**. This means they are ways of grouping the code we want to run. 

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

Some interesting features for procs:

* We can pass the proc to a method using `&`:

```ruby
cube = Proc.new { |n| n ** 3 }
[ 1, 2, 3 ].map(&cube)
# ==> [ 1, 8, 27 ]
```

* You can call a proc without a method by using `call`:

```ruby
greeting = Proc.new { puts "Hello!" }
greeting.call
# ==> Hello!
```

* You can convert symbols to procs using `&`:

```ruby
strings = [ "1", "2", "3" ]
nums = strings.collect(&:to_i)
# ==> [ 1, 2, 3 ]
```

## Differences between blocks and procs

1. Procs are **objects**, blocks are not.

The fact that procs are objects means that :
* we can call methods on it (like `call`)
* we can assign it to variables
* procs can return themselves

```ruby
p = Proc.new { puts "Hello!" }  # ==> #<Proc:0x00000000012b98e0@(irb):1> 
p                               # ==> #<Proc:0x00000000012b98e0@(irb):1> 
a = p                           # ==> #<Proc:0x00000000012b98e0@(irb):1> 
p.call                          # ==> Hello!
```

In contrast, blocks are just part of the **syntax** of a method call. It doesn't mean anything on its own and can only appear in an arguments list.

2. At most, only one block can appear in an argument list. However, a method can accept multiple procs.


http://awaxman11.github.io/blog/2013/08/05/what-is-the-difference-between-a-block/
https://www.synbioz.com/blog/block_proc_lambda_ruby
