# Destructive Methods and Bang `!` Suffix

## General case

Usually, the `!` (bang suffix) at the end of a method indicates that the method will permanently alter the caller.

```ruby
# Without !

irb :001 > a = [1, 3, 8, 9]
 => [1, 3, 8, 9] 
irb :002 > a.map { |n| n ** 3 }     # "map" returns the array modified by the block
 => [1, 27, 512, 729] 
irb :003 > a                        # "map" doesn't alter the original array
 => [1, 3, 8, 9] 
 
# With !
  
irb :004 > a.map! { |n| n ** 3 }    # "map!" returns the array modified by the block
 => [1, 27, 512, 729] 
irb :005 > a                        # "map!" mutates the caller
 => [1, 27, 512, 729] 
```

## Exceptions

However, **the bang suffix does not always equate to a destructive method** (ie. that mutates the caller).

* Some methods with a bang suffix are not destructive;
* Methods without a bang suffix can be destructive (eg. `pop` or `push`).

```ruby
irb :002 > a = [1, true, 3.67, "a string"]
 => [1, true, 3.67, "a string"] 
irb :006 > a.pop                    # "pop" returns the last element & permanently alters the array
 => "a string" 
irb :007 > a
 => [1, true, 3.67]
 ```

The only way to be sure that a method is destructive is to check the Ruby documentation or play around on irb.

----
TIL #7 - 30/04/2019
