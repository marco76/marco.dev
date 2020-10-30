---
published: true
title: 'Java Text Blocks - Quick intro'
description: 'Java 15 new features. Java Text Blocks example'
date: 2020-10-29T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'java'
color: '#7AAB13'
permalink: /java-text-blocks
categories:
  - Java
tags:
  - Java

introduction: 'Text blocks - Java 15 new feature'
---

Java 15 introduce the _Text Blocks_ as feature.

Text blocks were initially planned for Java 12 but this feature generated a lot of debates inside the Java Community and it's introduction has been postponed.
After being in _preview_ in JDK 13 and 14 it's the Prime Time for Text Blocks.
It's now an official feature of Java.

Official [JEP 378](https://openjdk.java.net/jeps/378)
Oracle's [Programmer's Guide to Text Blocks](https://docs.oracle.com/en/java/javase/15/text-blocks/index.html)

Why they are introduced? (Official goals)
> Simplify the task of writing Java programs by making it easy to express strings that span several lines of source code, while avoiding escape sequences in common cases.
  
> Enhance the readability of strings in Java programs that denote code written in non-Java languages.

### No string interpolation!
If you are a JavaScript developer you know how powerful are Template literals, e.g.
```javascript
 console.log(`For the user : ${user.id}, the sum is ${a + b}!`);
```

_Text block_ are not so powerful and they don't support string interpolation.

From the official JEP:

> Text blocks do not directly support string interpolation.
> Interpolation may be considered in a future JEP. 
> In the meantime, the new instance method String::formatted aids in situations where interpolation might be desired. 

### Multiline example

We can express easily multilines texts with a Text Block, a text block is a String included between two `"""` delimiters.

These snippets works on JShell:

```java
String java14 = "I like this Blog.\nIt show me some examples\nin Java and Angular!";

String java15 = """
        I like this Blog.
        It show me some examples
        in Java and Angular!""";

java14.equals(java15) // => true
```

### Escape char example

This can be useful if you need to use 'escaped' chars:
```java
String java14 = "I'd like a new post about \"Java 16!\"";

String java15 = """
I'd like a new post about "Java 16!" """;

java14.equals(java15); // => true

// Warning there is a 'space' after "Java 16!" in the text block. This space is part of the closing delimiters.
java15 = """
I'd like a new post about "Java 16!""""; // => ERROR: unclosed string literal
                                         //      ERROR: reached end of file while parsing
                                         //      Rejected ";
```
### New methods introduced in Java 15
Thanks to the TextBlocks _String_ gained some new methods in Java 15.

[Source Code String](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/lang/String.html)

`public String stripIndent()`
> Returns a string whose value is this string, with incidental white space removed from the beginning and end of every line.

`public String translateEscapes()`
> Returns a string whose value is this string, with escape sequences translated as if in a string literal.

`public String formatted(Object... args)`
> Formats using this string as the format string, and the supplied arguments.
