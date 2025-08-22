---
layout: post
title: Two Dimensional Text Parser Written in Elixir Using Nx

---


Ladder logic is a graphical programming language popular in industrial automation. It was developed to look similar to electrical schematics, allowing electricians to fault find issues.
Most ladder logic development software is proprietary and closed source to maximise vendor lock in. Sometimes there is an escape hatch. You are lucky if you can export to xml. Sometimes printing to a text file is the best you can manage. Then it is time to roll up your sleeves and translate it to something more flexible.
Traditional parsing (converting a string of text to a structure the computer understands) deals with a single line of text, that is interpreted linially. You can move forward or backward on the line to determine meaning, but you only move in one dimension. In the case of ladder logic output in ASCII text, a single instruction can span multiple lines, where white space and line breaks are significant. I couldn't work out how to parse something like this using traditional techniques, but had a breakthrough when I considered the text as you would intuitively as something in two dimensions where you not only read left to right to determing meaning, but also up and down.

In elixir, an ASCII character is stored as a number. A line is a list of characters. A multiline instruction is a list of lists, or a matrix. Conceptually the matrix can be scanned for occurances of symbols. This list of symbols could then be converted into an Elixir statement.

<!-- Why parse ladder logic? PLC's are computers. Computers are programmed in different languages. There are benifits to being able to translate from one language to another. If you know what the PLC is programmed to do, you can program a new PLC to do the same thing. You can also output artefacts along the way like flow charts and sequence diagrams. -->

Below are a series of simple ladder logic rungs with their elixir equivalent beneth.
```
|     X1                                Y1       
[------] [------------------------------(   )----
Elixir: Y1 = X1
```
```
|     X1                                Y1       
[------]/[------------------------------(   )----
Elixir: Y1 = not X1
```
```
|     X1            X2                  Y1       
[------] [-----------] [----------------(   )----
Elixir: Y1 = X1 and X2
```
```
|     X1            X2                  Y1       
[------] [----+------] [----------------(   )----
|             |                                  
|     X3      |                                  
[------]/[----+                                  
Elixir: Y1 = (X1 or not X3) and X2
```
Nx is ideal for this situation as a rung of text can be converted to a tensor, an the tensor can be scanned for occurances of a symbol and the structure can be converted to valid elixir syntax, which can then be convert to an abstract syntax tree, and manipulated to created documentation, digrams, or even a translation to a different PLC programming dialect.

Below is the last rung converted into a tensor.
```
#Nx.Tensor<
  s64[rows: 5][columns: 49]
  [
    [124, 32, 32, 32, 32, 32, 88, 49, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 88, 50, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 89, 49, 32, 32, 32, 32, 32, 32, 32],
    [91, 45, 45, 45, 45, 45, 45, 93, 32, 91, 45, 45, 45, 45, 43, 45, 45, 45, 45, 45, 45, 93, 32, 91, 45, 45, 45, 45, 45, 45, 45, 45, 45, 45, 45, 45, 45, 45, 45, 45, 40, 32, 32, 32, 41, 45, 45, 45, 45],
    [124, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 124, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32],
    [124, 32, 32, 32, 32, 32, 88, 51, 32, 32, 32, 32, 32, 32, 124, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32],
    [91, 45, 45, 45, 45, 45, 45, 93, 47, 91, 45, 45, 45, 45, 43, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32]
  ]
>
```
This matrix can be scanned to find occurances of 
```
---]  [---
```
or 
```
#Nx.Tensor<
  s64[rows: 1][columns: 9]
  [
    [45, 45, 45, 93, 32, 91, 45, 45, 45]
  ]
>
```
If you scan line 2 of the first tensor, you will notice that pattern twice. I have been working on an example 