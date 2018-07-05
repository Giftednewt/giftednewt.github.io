---
layout: default
title: Lexical Analysis - Part 1
---
It's taken much longer than I'd hoped to get round to finishing off this post. There is always something going which has seen this put on the back burner. Since picking this back up I think I've edited it about a hundred times or so this week (almost edited this bit out too). I've also decided that there is too much to put into a single post to keep things as compact as I'd like I'll be splitting this into two parts. Hopefully the second part will come along quicker than this one.

So to recap, in the previous post in this series I discussed the phases of a compiler. In this post I'll be covering lexical analysis.

####What is lexical analysis?

Lexical Analysis is the phase of the compiler that takes the given input string and checks that all of the input is valid within the given language.

####How does it do it?
The lexical analyzer reads the input string from left to right one character at a time. It divides the input into substrings, these may also be referred to as lexical units or lexemes. These lexemes are then classified using token classes.

A token class identifies a specific type of substring in the language. In a programming language these token classes are things like identifiers, keywords, numbers, whitespace, etc. The combination of the token class and substring is known as a **token**. 

The following code sample shows an assignment operation for a variable in C#

```
myValue = 12;
```
As the lexer reads through this it builds up the substring until a token class is recognized. The substring is then categorized and the lexical analyser then repeats this across the rest of the input until it reaches the end of the input.

For our example above the lexical analyzer would categorize the input as follows:

```
<identifier,"myValue">,
<whitespace," ">,
<assignment,"=">,
<whitespace," ">, 
<integer,"12">,
<semicolon,";"> 
```
Now take this more complex example.
```
if (i == 12)
{
    x = 10;
}
else
{
    x = 0;
}
```
How does the lexical analyzer correctly classify the double equals in the input as an operator rather than an assignment token?

To do this the lexer uses a technique called "lookahead". As each character of the input is read, the lexer looks at the next character of the input to determine whether the current substring joined with that character would be accepted as a token class in the language. The lexer will always tokenize using the longest possible valid substring. This is know as taking the "maximal munch".

####How is it implemented?

Language specifications are written using Regular Expressions. Regular Expressions are created which define the valid characters for each token class in the language. These regular expressions are then transformed into state machines called Non-deterministic Finite Automata (NFA) and Deterministic Finite Automata (DFA). These state machines are then used when reading the input to determine which tokens are valid for the substrings of the input.

In the next post I'll cover the usage of regular expressions in defining a language specification and how these are transformed into either the NFAs or DFAs that will be used by the lexer.

