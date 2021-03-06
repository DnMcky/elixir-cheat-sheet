# My Elixir Cheat Sheet For New Programmers

## Glossary of terms

### Module
A group of several functions

_How to identify_:
* There ~~will~~ should only be one module per ```.ex``` file (this is convention so may not be adhered to in 100% of cases)
* It will (always) look like this:
```
  defmodule Path.To.Module do
    # Find a bunch of functions here
  end
```
  _note_: the ```#``` you see in the code example above denotes a comment. Comments are lines in the code that are not executed and usually describe the next line in the programme.

  _Source_: [Elixir Getting Started](http://elixir-lang.org/getting-started/modules.html)

### Function
A block of code that performs a specific task. It will take input in the form of arguments (can sometimes be 0 arguments, meaning no input is required) and respond with an output. 

* There can be many functions in a module.
* There are several ways to define a function in elixir.

#### Public Function
A function defined in one module that can be used in another

_How to identify_:
* A public function will typically look like this:
```
  def cool_function_name(parameter) do
    "Hello, " <> parameter
  end
```
* Or it will look like this:
```
  def cool_function_name(parameter), do: "Hello, " <> parameter
```
_note:_ the easiest way to identify a typical function is the ```def do```

#### Private Function
A function that can only be used in the module that it is defined in

_How to identify_:
* A private function will typically look like this:
```
  defp cool_function_name(parameter) do
    "Hello, " <> parameter
  end
```
* Or it will look like this:
```
  defp cool_function_name(parameter), do: "Hello, " <> parameter
```
_note:_ the easiest way to identify a private function is the ```p``` after ```def```

#### Anonymous Function
A function that does not have a name

_How to identify_:
* An anonymous function looks like this:
```
  sum = fn (a, b) -> a + b end
```
_note:_ the ```->``` can be seen as is the replacement for do in a regular function

#### The & shorthand
A shorthand version of anonymous functions

_How to identify_:
* It will look like this:
```
  sum = &(&1 + &2)
```
_note:_ ```&1``` and ```&2``` show how the paramters are made available

  _Source_: [Elixir School](https://elixirschool.com/lessons/basics/functions/)

### Arity
Functions all have an arity. Arity is the number of paramters that a function expects.

Even if two functions have the same name, they are considered different if their arity is different.

For example `hello/0` is a different function to `hello/1`, this is especially important when thinking about pattern matching.

If a function takes 2 paramters it has an arity of 2 eg.
```
  def arity_two_function(parameter_one, parameter_two) do
    parameter_one <> parameter_two
  end
```
_note:_ you will often see a function referred to like ```function/3```, this means that the function function has an arity of 3

### Paramter
A parameter is a variable that is passed into a function (also known as an argument)

### Variable
A variable is a value stored against a variable name

In Elixir a variable can assigned more than once. However when we pin(^) a variable we are saying that we want the value to be what we set it to previously. The = in this case is a pattern match, as can be seen below there is no match as a is currently 2.
```
  iex> a = 1
  1
  iex> a = 2
  2
  iex> ^a = 3
  ** (MatchError) no match of right hand side value: 3
```
  _note:_ in the example above the ```^``` is known as the pin operator. It is used to access the previously bound(assigned) variable.

  _Source_: [Elixir Lang](http://elixir-lang.org/crash-course.html#variable-names)

###### A pretty awesome explanation of the above
In Elixir the `=` operator doesn't do assignment it pattern matches, sometimes resolving that match through assignment. That’s why it’s called the _match_ operator. This also means that variables aren’t really places in memory that values are stored in, but rather _labels_ for the values. That is, Elixir/Erlang allocates memory for the values, not the variables.

_Source_: [Steven Vandevelde - Medium Blog](https://medium.com/making-internets/functional-programming-elixir-pt-1-the-basics-bd3ce8d68f1b#.by1sux69o)

## Some Basics of Functional Programming in Elixir (not exclusive to Elixir)

### Pure Functions

A function is considered pure if it will always give the same output, given the same input and it does not cause any side-effects.

### First-class Functions

In functional programming we often refer to first class functions. Simply put we mean that a function can be treated like any other variable.

```elixir
function = fn(x) -> x * 2 end
```

### Higher-order Functions

You can also pass functions as arguments to other functions. This is an effect of functions being treated as first class.

```elixir
Enum.map([1, 2, 3], fn(x) -> x * 2 end)
```

### Closure

Closure is reliant on functions being first class. The differentiating feature however is that the variables that were in scope when the function was called will still be accessable.

```elixir
a = 10

closure = fn() -> IO.puts a end

closure.()

a = 20

closure.()

# Output:
# 10
# 10
```

### Immutable State

Elixir is immutable. This eliminates cases where multiple entities can change a data structure.
```
iex> tuple = {:ok, "hello"}
  {:ok, "hello"}
  iex> put_elem(tuple, 1, "world")
  {:ok, "world"}
  iex> tuple
  {:ok, "hello"}
```
However you can re-assign variables. Although you can see the hat/pin(`^`) stopping that and throwing the `no match` error.
```
  iex> a = 1
  1
  iex> a = 2
  2
  iex> ^a = 3
  ** (MatchError) no match of right hand side value: 3
```

## List of ___possibly___ awesome resources

[A community driven style guide for writing Elixir](http://elixir.community/styleguide)
