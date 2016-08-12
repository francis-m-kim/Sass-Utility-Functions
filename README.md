#Sass Utility Functions

Nothing special here, just a bunch of functions that I thought might be useful to have in SASS. To use them in your project, simply download the utils folder and utils.scss file and `@import path/to/utils`.

##List Functions

The list_functions.scss file includes definitions for the following functions:

* `is-list($object)`: a predicate function for lists.

*  `is-empty($object)`: a predicate that tests whether a list (or map) is empty.

*  `range($start, $end, $step: 1, $inclusive: true)`: creates a list of numbers from start to end. `$step` and `inclusive` parameters are optional.

*  `first($list)`: returns first item in list.

* `last($list)`: returns last item in list.

* `rest($list)`: returns all but the first item in list.

* `slice($list, $start, $length: length($list) - $start + 1)`: returns a slice of the list from `$start` index. Length of slice can be specified but defaults to the end of the list.

* `insert($list, $item, $index)`: returns a new list with `$item` inserted at the given index. If the index is out of bounds on either side, the item is prepended or appended.

* `replace($list, $old, $new)`: returns a new list with all instances of `$old` replaced with `$new`.

* `remove($list, $item)`: returns a new list with all instances of `$item` removed.

* `remove-nth($list, $n)`: returns a new list with the `$n`-th item removed. Complements built in `set-nth` function.

* `remove-every-nth($list, $n, $start: 1)`: returns a new list with every `$n`-th item removed. If optional `$start` parameter is not specified it defaults to the beginning of the list.

* `reverse($list)`: reverses the list.

* `map($list, $func)`: returns a new list where the specified function has been applied to every item of a list. For example, let `$list: 1 2 3` and `$func: addOne` where `addOne` has already been defined as `@function addOne($x) { @return $x + 1; }`. map($list, addOne) returns `2 3 4`. `$func` should take one argument.

* `filter($list, $func)`: takes a list and a boolean function and returns a list where all items which cause the function to return true are retained. For example: we define `@function isEven($x) { @return if(x % 2 == 0, true, false)}`. filter(range(1,10), isEven) will return `2 4 6 8 10`.

* `reduce($list, $func, $base: 0)`: reduces a list to a single value by recursively calling the function on the base value and the successive items of the list and reassigning the base value to the result. `$func` should take two arguments. Say we define `@function mult($x, $y) { @return $x * $y; }` and `$list: 1 2 3`. `reduce($list, mult, 1)` will return 6.

* `list-average($list)`: takes a list of numbers and returns the average. A simple average function which only takes two numbers can be found in the number_functions.scss file.

* `change-separator($list, $separator: " ")`: changes the separator of the list.
 `change-separator(hello world, "-")` will return `hello-world` which is of course no longer a list.

* `list-to-string($list, $separator: " ")`: same as `change-separator` but surrounds the result in quotes. Would have called this function "join" but the name was already taken.

* `lists-to-map($key-list, $val-list)`: returns a map whose key-value pairs are taken from `$key-list` and `$val-list`. The function returns when it runs out of keys.


##Number Functions

The number_functions.scss file includes definitions for the following functions, which are all pretty self-explanatory:

* `is-num($object)`
* `average($num1, $num2)`
* `expt($num, $power)`: takes both positive and negative powers.
* `sqr($num)`: square the number.
* `sqrt($object)`: square root implementing Newton's method.


##String Functions

The string_functions.scss file includes definitions for the following functions:

* `is-string($object)`

* `get-char($str, $idx)`: Get character at specified index.

* `str-trim($str)`: Remove blank spaces from both ends of the string.

* `str-append($str1, $str2, $separator: "")`: Adds `$str2` to the end of `$str1`. If separator is not specified, the strings are joined with no space.

* `str-prepend($str1, $str2, $separator: "")`: Adds `$str2` to the front of `$str1`. Once again, if separator is not specified, the strings are joined with no space.

* `str-remove($str, $remove)`: Removes every instance of `$remove` within `$str`. For example, `str-remove("hello world", "o")` returns `"hell wrld"`.

* `str-replace($str, $old, $new)`: Replaces every instance of `$old` with `$new` in `$str`. E.g., `str-replace("hello world", " ", "*")` returns `"hello*world"`.

* `str-split($str, $splitter: " ")`: Returns a list of the string split at every instance of the splitter. E.g., `str-split("hello world", "l")` returns '"he" "o wor" "d"'.


##Map Functions

The map_functions.scss file includes definitions for the following functions:

* `is-map($object)`
* `map-to-list($map)`: Flattens a map into a list in a depth-first manner.
* `map-depth($map)`: Returns the nesting depth of a map.
* `map-deep-get($map, $get)`: Returns the value associated with a key nested arbitrarily deep within a map.



Hope these help. *Stay sassy!*
