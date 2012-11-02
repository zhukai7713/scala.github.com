---
layout: overview-large
title: Overview

partof: reflection
num: 1
outof: 6
---

**Eugene Burmako, Heather Miller**

*Reflection* is the ability of a program to inspect, and possibly even modify
itself at runtime. It has a long history across object-oriented, functional,
and logic programming paradigms, with each paradigm evolving its own,
sometimes markedly different, *status quo* for reflection. While more
functional programming languages like Lisp/Scheme have focused primarily on
reification to enable tasks like dynamic interpretation, object-oriented
programming languages like Java have focused primarily on runtime reflection to
enable tasks like the inspection and/or invocation of class members at runtime.

Three principal use cases of reflection across languages and paradigms are:

1. **Runtime Reflection**. The ability to inspect and invoke runtime types and their members.
2. **Compile-time Reflection**. The ability to access and manipulate abstract syntax trees at compile time.
3. **Reification**. The generation of abstract syntax trees at runtime in the case of (1), or at compile time in the case of (2).

Until 2.10, Scala has not had any reflection capabilities of its own. Instead,
one could use Java reflection which provided a very limited subset of runtime
reflection capabilities from point (1) above. Many Scala-specific types are
simply unrecoverable under standalone Java reflection; including info about
runtime existential, higher-kinded, path-dependent and abstract types. In
addition to these Scala-specific types, Java reflection is also unable to
recover runtime type info of Java types that are generic at compile-time; a
restriction that carried through to runtime reflection on generic types in
Scala.

In 2.10, Scala Reflection was introduced not only to address the shortcomings
of Java's runtime reflection on Scala-specific and generic types, but to also
add a more powerful toolbox of general reflective capabilities to Scala. Along
with full-featured runtime reflection for Scala types and generics (1), 2.10 also
ships with compile-time reflection capabilities, in the form of
[Scala Macros]({{site.baseurl }}/overviews/macros.html) (2), as well as the
ability to *reify* Scala expressions into Scala abstract syntax trees (3).

## Runtime Reflection
In Scala runtime reflection, you can get types. Whereas in Java, you can only get classes.
`isAsssignableFrom` - is B a subclass of A (you can do basic subtyping checks with Java)
`getType` returns a `Class` object
^ is this a valid point to make still?

- Get around erasure with Scala reflection.

#### Classes vs Types

Why are types more powerful than classes
^ is this a valid or worthwhile point to make?

Java's type system is so simple that a class is essentially a type- the only exception is when you have generic types. This use case isn't fully supported by Java reflection.

In Scala, one can create an array of a generic type in Scala but not in Java- it uses reflection (i.e. ClassTags) only internally.

If you use Java reflection, you get a view that's restricted to what can be represented in a Java `Class` instance.
For example, I can't find the self type of a trait that I'm examining using Java reflection.

### Some Examples

What is meant by runtime reflection. Examples.
Some of the typical things that you can do with Scala reflection. This should also list things that aren't possible to do in Java.

## Compile-time Reflection

Macros. Brief intro.
Reflection is the window to *Metaprogramming*, the ability for programs to modify themselves at runtime. Scala macros are an example of this.

### Some Examples

## Preliminaries
### Universes
### Mirrors

## TypeTags/ClassTags Generic Arrays

    def m[T: TypeTag](x: T): Unit = {
      ...
    }

This is a use of reflection because you're explicitly requesting to get runtime type information for T.