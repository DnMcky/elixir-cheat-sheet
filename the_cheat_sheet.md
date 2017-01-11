# My Elixir Cheat Sheet For New Programmers

## Glossary of terms

### Module
A group of several functions

_How to identify_:
* There will only be one module per ```.ex``` file
* It will look like this:
```
defmodule Path.To.Module do
    #Find a bunch of functions here
end
```
_Source_: [Elixir Getting Started](http://elixir-lang.org/getting-started/modules.html)

### Function
A block of code that performs a specific task.

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
Functions all have an arity. Arity is the number of paramters that a function expects

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
_note:_ in
_Source_: [Elixir Lang](http://elixir-lang.org/crash-course.html#variable-names)

###### A pretty awesome explanation of the above
In Elixir the `=` operator doesn’t only do assignment, but also pattern matching. That’s why it’s called the _match_ operator. This also means that variables aren’t really places in memory that values are stored in, but rather _labels_ for the values. That is, Elixir/Erlang allocates memory for the values, not the variables.

_Source_: [Steven Vandevelde - Medium Blog](https://medium.com/making-internets/functional-programming-elixir-pt-1-the-basics-bd3ce8d68f1b#.by1sux69o)

## Things I didn't know about functional programming

## List of ___possibly___ awesome resources

[A community driven style guide for writing Elixir](http://elixir.community/styleguide)
