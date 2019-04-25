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

It is defined using `Proc.new`.

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

2. At most, only one block can appear in an argument list. However, a method can accept **multiple procs**.

```ruby
def multiple_procs(p1, p2)
  p1.call
  p2.call
end

a = Proc.new { puts "I am the first proc!" }
b = Proc.new { puts "... and I'm the second one." }

multiple_procs(a,b)

# I am the first proc!
# ... and I'm the second one.
```

3. Procs (as they are named) can be called over and over again without rewriting its definition. Blocks need to be re-written every time they are called.

## What are lambdas?

A lambda is a way to define a block and its parameters with some special syntax. Like procs, lambdas can be saved for later use.

Lambdas are defined using the following syntax:

```ruby
# Original syntax
greeting = lambda { |name| puts "Hello, #{name}!" }

# Since Ruby 1.9
greeting = -> (name) { puts "Hello, #{name}!" }
```

Some interesting lambda features:

* They can be called by `call`:
```ruby
greeting.call("Juliette")
# ==> Hello, Juliette!
```

* A lambda is a Proc object (like procs). 
```ruby
greeting.class
# ==> Proc
```

## Differences between procs and lambdas

1. Lambdas are sensitive to the number of arguments, while blocks are not.

A lambda will throw an error if you pass the wrong number of arguments. A block will ignore unexpected arguments or return `nil` if some arguments are missing.

```ruby
# Lambda
lambda = -> (n) { puts n }        # Creates a lambda that takes one argument
lambda.call(2)                    # Prints out 2
lambda.call                       # ArgumentError (wrong number of arguments (given 0, expected 1))
lambda.call(1,2)                  # ArgumentError (wrong number of arguments (given 2, expected 1))

# Proc
proc = Proc.new { |n| puts n }    # Creates a proc that takes one argument
proc.call(2)                      # Prints out 2
proc.call                         # Returns nil
proc.call(1,2)                    # Prints out 1, ignores 2
```

2. Lambdas and procs treat the `return` keyword differently

`return` inside a lambda triggers the code right outside the lambda (like a regular method).

```ruby
def lambda_behaviour
  lam = lambda { return }
  lam.call
  puts "Hello world"
end

lambda_behaviour
# Prints out "Hello world"
```

However, `return` inside of a proc triggers the code *outside the method where the proc is executed*.

```ruby
def proc_behaviour
  proc = Proc.new { return }
  proc.call
  puts "Hello world"
end

proc_behaviour
# Returns nil
```

----
TIL #5 - 24/04/2019
