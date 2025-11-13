# On Python

How is a programming language to be understood?

Labels like *interpreted*, *dynamic*, *static*, *compiled*, are very uninformative -- they do not
speak to the nature of a programming language.

All programming languages excluding Machine Code share one thing -- that they are translators
to machine code. Programming languages do not *need* to exist; a programmer, instead of using
Python, Go, or C, could very well achieve the exact same results through providing raw
machine instruction.
Why then do we have hundreds of programming languages, each offering a unique syntax & philosphy
on how one builds procedural definitions?

The primary reason for programming languages, which operate at a *higher level* than machine
code, is to *abstract* the layers of machine code, enabling programmers to reason about their
procedures outside of the consideration of the specific machine instruction that will execute
them.
Some programming languages offer a greater level of abstraction away from the machine than others.
Assembly language is a one-to-one mapping to Machine Code; every line of assembly instruction
corresponds to one machine instruction.
Python, on the other hand, has many layers of abstraction between the language and machine
code; to understand Python is to understand these layers of abstraction and the reason for
them.

## Types

A computer is made up of a few components -- CPU, RAM, Disk Memory, I/O slots. The execution of a process results in the RAM of a computer being occupied by many bits (1s and 0s).
To give meaning to the endless sea of bits in RAM, and to enable the composition of a program,
these bits are given structure. A computer may be an 8-bit, 6-bit, n-bit machine -- the integer
value associated with the bits results in the length of a *byte* in the machine.

RAM is then represented not as an endless sea of bits, but as a table of *word*-length bytes.
A *word* is a list of bytes with an associated length, which could form a machine instruction
for a given computer.
E.g, A computer may be an 8-bit machine, with a 5-byte word length.
RAM would then be a table of rows, where each row is 5 bytes, and each byte is 8 bits.

To deal with the architecture of the computer, languages take an approach of defining *Types*.
A type in a programming language correlates to an amount of bytes which would be assigned
in RAM.
This idea of *Types* enables programming languages to give programmers the ability to represent
high level things such as Numbers and Characters.

The following shows some types of the programming language *Go*, with what they represent:

```go
u8int // 0 - 255
s8int // -127 - 126
u16int // 0 - 65535
s16int // -32768 - 32767

var x u8int = 2 // 00000010 in machine code
```

These types offer programmers the ability to compose programs which adhere to mathematical
principles -- being able to represent entities such as Integers, Floating Numbers, Characters,
while also considering the implications of how their procedures will map to the RAM of the
computer they are running their program on.

### Types in Python

Python, as a language, offers an interface to the programmer which hides the machine from the
computer. Python offers the programmer a single type, *The Object*.

Instances of objects created in Python will indeed result in RAM being assigned at the machine
level, but the properties of how much memory & the order of which the procedures will be
executed are effectively hidden from the composer of a Python program.

The guiding principle behind this idea is to give the programmer a mutable sandbox -- an
environment not constrained by types or runtime execution, where the programmer can represent
entities which map to their conception of reality.
All programs in Python are translated into a format called bytecode & then ran on a
virtual machine written in C, before then being translated from this virtual machine to the
actual machine running the computation.

While providing a supposed benefit of *creativity*, the programmer no longer understand how
their program's entities or procedures are represented at the machine level.
A Python programmer doesn't know how much bytes in RAM an integer with the value 7 occupies,
nevermind the specific bits which represent it.

In Python everything is of this *object* type -- functions, numbers, strings, classes. Python
holds the philosophy that it does not matter how things are represented at the machine level,
what matters is how *nice* things feel for the programmer.

Python too does not necessarily care about the style in which the programmer chooses to implement
their programmers; though having certain *idioms*, Python does not explicitly enforce a
functional nor object-oriented approach.

## Interpretation & Imports

Given a Python file, the Python *interpreter* will interpret all lines of code, recursively
following back all imported modules, to effectively result in one big single script which is
fed into the Python Virtual Machine.
This works fine with limited files -- but when many modules in Python are dependent on the
same modules, it results in a very difficult struggle to structure your project in a way which
does not break things due to circular imports.

The Python programmer then, when composing a large project, is forced to deal with the structural
state of where their *objects* are placed in relation to the main entrypoint of their program.

This is a difficult thing to grapple with, especially on projects with multiple programmers.

Due to these interpretation & translation mechanisms in Python, tied together with the syntactic
structure of the language, Python also becomes a very difficult language to build concurrent programs in. 

## Use

From the points noted above, Python can be thought of as a language which can be used to build
anything you can really think of -- aslong it is sequential and you are willing to grapple with the structural
state of how your program will be interpreted.

Do you care about representing entities which will map to a set number of bytes in your machine?
Don't use Python.

Do you want to build a concurrent distributed system?
Don't use Python.

Do you not care about any of that and you just want to build a little program where you can
have fun with list comprehensions?
If so, Python is perfect for you :)
