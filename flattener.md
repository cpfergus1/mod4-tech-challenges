# Problem - Array Flattener
![recursion](https://media.giphy.com/media/3GuP496Wrkos8/giphy.gif)

Imagine you have a deeply nested array, or multi-dimensional array, like this:

```rb
 array_of_ints = [1, 2, 3, [[4], 5], [[[6]]]]
 array_of_strings = ["hi", "this is", [[["string"], "that is very"], [[[["nested"]]]]]]
```
the contents of the array aren't important.

In Ruby and JS, we have built in methods and functions to `flatten` arrays into one dimension.  For example, in Ruby:

```rb
=> [1, 2, 3, [[4], 5], [[[6]]]]
[8] pry(main)> array_of_ints.flatten
=> [1, 2, 3, 4, 5, 6]
```
and in JS:

```js
> arr1
[ 0, 1, 2, [ 3, 4 ] ]
> arr1.flat()
[ 0, 1, 2, 3, 4 ]
```
If we look at the docs for either of these, we notice that they are _recursive_ by nature. Your goal is to recreate this functionality by writing a recursive function to accomplish this same thing. For example:

```rb
 array_of_ints = [1, 2, 3, [[4], 5], [[[6]]]]
=> [1, 2, 3, [[4], 5], [[[6]]]]
ruby_flattener(array_of_ints)
=> [1, 2, 3, 4, 5, 6]
```
or in JS:

```js
> arr1
  [ 0, 1, 2, [ 3, 4 ] ]
> flatten(arr1)
  [ 0, 1, 2, 3, 4 ]
```

# Instructions

1. Copy this markdown and paste in your own, privte gist
2. In your private gist, fill out the questions below
4. Submit by the due time as instructed in Zoom


## Rewrite the question in your own words:

flatten all arrays!

## What assumptions will you make about this problem if you cannot ask any more clarifying questions? What are your reasons for making those assumptions?

array length doesn't matter

## What are your initial thoughts about this problem? (high level design, 2-3 sentences)

itterate through array and shift out elements into a new array. Find out if the element is an array, if the element is an array, run method again until there are no more array elements.

## How would you identify the elements of this problem?

- [x] Searching of Data
- [ ] Sorting of Data
- [ ] Pattern Recognition
- [ ] Build/Navigate a Grid
- [ ] Math
- [ ] Language API knowledge
- [x] Optimization


## Which data structure(s) do you think you'll use? What pros/cons do you see with that choice?

arrays - seems like the best choice to solve this problem. 

## Write out a few lines of initial pseudocode: (mid-level design, NOT REAL CODE)
```
def flatten_array(array)
 return new_array if array.length == 0 # break method if original array is gone
 element = array.shift #take out first element
 if element is an array
  flatten_array(element) #flatten that element
 else
  shovel value into new array
 end
 flatten_array(array) # rerun method until there are no more elements
end
```
 

## Write out any implementation code OR link to repl

https://repl.it/join/urtdnqdc-connorferguson
```
class Flattener

  def flatten(array, new_array = [])
    return new_array if array[0].nil?
    element = array.shift
    if element.class == Array
      flatten(element, new_array)
    else
      new_array << element
    end
    flatten(array, new_array)
  end

end


arr = [1, 2, 3, [[4], 5], [[[6]]]]
flattener = Flattener.new
new_array = flattener.flatten(arr)
print new_array

string_arr = ["hi", "this is", [[["string"], "that is very"], [[[["nested"]]]]]]
new_array = flattener.flatten(string_arr)
puts 
print new_array
```
## What is the Big O complexity of your solution?

I believe this is O(n^2) since I am interating over each element and then running the function again if it is another array. 
