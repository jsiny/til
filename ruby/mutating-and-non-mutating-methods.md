# Mutating and Non-Mutating Methods

## Introduction

Methods can either be mutating or non-mutating.
Furthermore, a mutating method can be mutating with respect to the receiver, but not with respect to the other arguments.

## Definitions

### Non-Mutating Methods

A method is said to be **non-mutating** with respect to an argument if it does **not** modify that argument.

*Note:* All methods are non-mutating with respect to **immutable objects** (eg. boolean values or numbers).

### Mutating Methods

Quite logically, a **mutating** method is therefore a method that *does* modify that argument (usually, its receiver).

*Note:* Very few methods mutate other arguments than their receivers. 

## Examples of Non-Mutating Methods

### Simple Assignment

Assignment merely tells the program to bind an object to a variable.
Assignment connects the variable to a new object without changing the object.

```ruby
def some_method(input)
  input = 'New value'
end

a = 'Initial value'

b = some_method(a)
# => 'New value'

a
# => 'Initial value'
# `a` 's value wasn't changed because assignment is non-mutating.
```

### Assignment Operators

Assignment operators (`+=`, `-=`, etc) are also non-mutating.

```ruby
def add_one(num)
  num += 1
end

a = 3

add_one(a)
# => 4

a
# => 3
```

## Examples of Mutating Methods

### Indexed Assignment

Although indexed assignment *looks* like regular assignment, the `#[]` is actually mutating. 

```ruby
def change_second_char(input)
  input[1] = '*'
  input
end

word = 'Hello'

change_second_char(word)
# => 'H*llo'

word
# => 'H*llo'
# The variable `word` still references the same String,
# but the String was modified by the indexed assignment
```

### Concatenation

Although the `#<<` and `+=` operators both perform concatenation,
they have one major difference: `#<<` is mutating, while `+=` (like all assignment operators) isn't.

```ruby
def concat(input)
  input << "_world"
end

a = 'hello'

b = concat(a)
# => 'hello_world'

a
# => 'hello_world'
# a was mutated
```

### Setters

Setters are methods that are defined to modify the state of an object (usually by modifying an instance variable).

```ruby
person.name = 'Bill'
```

----
TIL #10 - 25/05/2019
