# Parallel Assignment

Let's assume you want to swap those two variables' values.

```ruby
a = 1
b = 2
```

One solution could be to use a temporary variable.

```ruby
temp = a
a = b
b = temp

p a, b
# => [2, 1]
```

However, it's a bit long and cumbersome.

Ruby offers instead a better alternative: the parallel assignment.
It allows to assign at the same time two variables (both actions are performed
in parallel).

Therefore, you can write:

```ruby
a, b = b, a

p a, b
# => [2, 1]
```

Voilà!

----------
TIL #11 - 08/06/2019
