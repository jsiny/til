# What are `break` and `while`'s return values?

## Default return values

In Ruby, a method always returns exactly one object. A method can return `nil` (which means "nothing at all"), but it's still considered an Object by Ruby.

`break` and `while` usually return `nil`:

### Break

```ruby
result = while true
  break
end

p result
# => nil
```

### While

```ruby
a = 0

while a < 5 do
  p a
  a += 1
end
```

Output: 
```ruby
0
1
2
3
4
=> nil 
```

## Special case

However, `while`'s return value is `nil` *unless `break` is used to supply a value*. In that case, `while` returns that value passed to `break`.

### Break

```ruby
result = while true
  break 5
end

p result
# => 5
```

### While

```ruby
i = 0
 
while i < 5
  puts i
  i += 1
  break i if i == 2
end
```

Output:
```ruby
0
1
 => 2       # The value passed to break
 ```

------
TIL #8 - 09/05/2019
