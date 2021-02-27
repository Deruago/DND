# DND
Deamer Natural Deduction, is a language used to natural deduce abstract propositions.

Its purpose it to check wether an abstract proposition is a tautology.

## DeamerProject
DND is created using the DeamerProject. DeamerProject is a compiler generation infrastructure, used to easily create languages.

## Roadmap
Currently this is in the starting phase, and will most likely don't do anything. Whenever a working prototype is available, you are able to get it from the releases page as a "Pre-Release".

# Usage

## Basic propositions

Basic propositions are any form of standard abstract propositions. You can define a simple proposition as follows:

```DND
\ All the possible simple operations
a and b
a or b
a => b
a <=> b
a = b
```

## Comparisons (mathematics)

You can also use comparisons such as greater than or less than. E.g.:

```DND
\ All the different comparisons
a >= b
a > b
a <= b
a < b
```

## Arithmetic (mathematics)

You can also use arithmetic, E.g.:

```DND
\ All the different basic arithmetic operations
a + b
a - b
a * b
a / b
a ^ b
```

## Complex propositions

If you want to define some more complex propositions, other than `A and B` , you are required to use '(' and ')', E.g.:

```DND
(a and b) or ((not a) and (not b))
```

By putting some expression inside parenthesis, you create a new value, which enables you to use another operation.

## Predicates

DND also supports predicates. Currently we support 2 quantifiers:

- universal
- ,and existential

You can use them as follows:

```DND
\ universal quantifier
for all [ Var x in Naturals : x + 1 > x]

\ existential quantifier
there is [ Var y in Integers : y ^ 2 = 0]
```

You can also combine quantifiers with other quantifiers:

```DND
for all [ Var x in Naturals : there is [ Var y in Integers and (x != y) : y < x]]
```

## Functions

You can define your own functions, or predefined functions. There are also ways to import functions.

You can call a function just like you will do in most other languages:

```DND
\ Set some var x, to be the output of function "RandomInteger()"
Define Var X = RandomInteger()

\ Print 20
Print(20)

\Print the variables X, y, and z
Print(x, y, z) 
```

Defining your own functions is also very similar to most other languages:

```DND
\ Check if the Truth functions are not the same by all
\ Returns True or False
Define Function disjoint(a, b, c)
{
	(a != b) and ((a != c) and (b != c))
}

\ x1 is a tautology
Define Var x1 = True

\ y1 is a contradiction
Define Var y1 = False

\ z1 is some abstract proposition
Define Var z1

Define Var X = disjoint(x1, y1, z1)
```

Importing functions is described in the section "Import"

## Import

You can import other libraries, this is useful whenever you don't want to write a specific piece of repetitive code, which is defined in another library.

Importing can be done as follows:

```DND
Import SomeLibrary
```

All functions from "SomeLibrary" will be available to use in the file you imported the library.

## Comments

As you may have noticed, we used a lot of the character '\\', this character is used for commenting in your code. The '\\' is a single line comment.

If you want to use multi line comments you need to use "\\\*                \*\\".

E.g.:

```DND
\ This is a single line comment
for all[Var x in Naturals : ] \ I can put everywhere 
\ , but will only cover one line

\*
But I can go
over multiple lines!
*\
```

But note it is not used to "comment" code, whenever you do this you risk on getting incorrect output, or uncompilable code. So please refrain of using '\*' and '\\' unnecessarily in the comment blocks, use them only for starting and ending.

## Sets

You can create sets as follows:

```DND
Define Var SomeNumbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
```

You can create sets of nearly everything:

```DND
Define Var ExampleOfComplexSets =
{
	disjoint(1, 2, 3),
	{
		{0, {}, {2, 3, 4, 5}, 6, 7, 8, 9, 10}
	}
}
```

## Set logic

The following operations and comparisons are defined for sets:

```DND
Define Var Universe = Naturals
```

