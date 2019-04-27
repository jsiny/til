# Variables Initialized inside a Method are Unavailable Everywhere Else

A variable's scope determines where in a program can a variable be accessed and used. 
A variable's scope is defined by **where the variable is created**. 

There is an extremely important rule about variable's scopes: **Inner scope can access variables initialized in an outer scope, but not vice versa.**

```ruby
outer_var = 5

2.times do |n|
  outer_var = 2
  inner_var = 9
end

puts outer_var     # Prints 2 because it could be accessed inside the method
puts inner_var     # Prits nil because it cannot be accessed from outside the method
```

Trying to access an inner variable from outside returns the following error:
```bash
undefined local variable or method `x' for main:Object (NameError)
```

---
TIL #6 - 27/04/2019
