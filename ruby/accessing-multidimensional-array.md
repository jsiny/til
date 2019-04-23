# Accessing a multidimensional array

## Accessing an element in a one-dimensional array

Each element of an array has an **index**. The first element of the array has index `0`, the second one `1`, etc.

To retrieve an element of an array, type `array[index]`:

```ruby
my_array = [ true, 356, "Hello" ]
my_array[1]                         # Retrieves 356
```

## The multidimensional array situation

However, when it comes to multidimensional arrays, things are not so simple.

```ruby
recipes = [ [ "lettuce", "tomato", "mozzarella" ], [ "pasta", "bolognese" ], [ "pizza", "anchovies", "pineapple" ] ]
```

If I type `recipes[0]`, the program will return the whole array `[ "lettuce", "tomato", "mozzarella" ]`.

However, if I only want to access `mozzarella`, I can type: `recipes[0][2]` (ie. the third element of the first array).

---
TIL #4 - 23/04/2019
