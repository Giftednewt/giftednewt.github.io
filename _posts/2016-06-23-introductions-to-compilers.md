---
title: Introduction to compilers
---
Since making a few, albeit minor contributions to the [Roslyn](http://www.github.com/dotnet/roslyn) project I have felt that I need a more in-depth understanding of how a compiler works. My understanding is very basic. Yes, I understand that a compiler takes the code that I write and turns that into some form of lower level instructions that are ultimately executed. But how? What are the different parts of the process? How do they fit together? 

After searching around on the web I found the [compilers](http://lagunita.stanford.edu/courses/Engineering/Compilers/Fall2014/about) course on the Stanford University site and started down the road to discovery. This post is intended as a personal exercise to validate to myself that I have understood what I have learnt and in the process maybe help others understand too.

So what have I learnt so far? 

A compiler is made up of 5 phases, these are:
1) Lexical analysis
2) Parsing
3) Semantic analysis
4) Code generation
5) Optimization

The first 3 phases are commonly referred to as the "front-end" of the compiler. Sometimes the first 2 phases are combined. Each phase of compilation has a specific job to do and works on the output of the previous phase (if one exists). 

Typically, if errors are found during a phase of the compilation process the compiler will attempt to complete that phase of compilation and then these are reported back to the user and the compilation is aborted. The main reason for attempting to complete the phase of compilation before reporting errors back is that a program can potentially contain many errors and if the compilation always failed on the first error it would waste a lot of time for the user as they have to fix the error and then attempt compilation again only to find there was another error further on in the code.

Stay tuned for the next post in this series where we will start looking at Lexical Analysis, the first phase of the compiler.