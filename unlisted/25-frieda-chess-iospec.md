---
layout: page
title: "2025 Frieda Chess Bot Competition - I/O spec"
permalink: /unlisted/25-frieda-chess-comp-io-spec
tags: ["25-frieda-chess-comp","iospec"]
description: " "
---

- [Return to competition main page]({% link unlisted/25frieda-chess-bot.md %})

# INPUT/OUTPUT Specification

Your program will read from stdin and outout to stdout (standard input output). **THE USE OF ANY OTHER FILE OPERATIONS WILL RESULT IN YOUR PROGRAM BEING KILLED**.

An unspecified ammount of time after startup, your program will receive a single line of input: either "white" or "black" (with a newline character at the end), indicating which color your bot will be playing.

If your program produces any output before this initial line, it will *most likely* result in disqualification by the automated judge. 
 
**YOUR PROGRAM SHOULD STILL NOT PRODUCE OUTPUT. DOING SO WILL RESULT IN DISQUALIFICATION**

The next line of input will have three space separated strings as follows:

```
<move> <time> <time> <state>
```

The first string is of format `<move>` and encodes the move preceding yours (ie: your opponnents movement). The second string is of format `<time>`, and is the ammount of time you have left. The third string is also of format `<time>` and indicate sthe ammount of time your opponent has left.

Your program must now respond with a move of their own, which shall be a single line of output of the form: 

```
<move>
```

The next line of input will be of form 

```
<status> <time>
```

## \<move\> - specifications 

The symbol `<move>` shall have one of four values:

- A sequence of four characters, where the first two indicate the starting position of the piece being moved and the last two indicate the position its attempting to move to. Valid as input AND output
- `O-O` indicating an attempt to castle kingside. Valid as input or output.
- `O-O-O` indicating an attempt to castle queenside. Valid as input or output.
- `NONE` this is a reserved value used by the judge to indicate no previous move happened (that is, your program is white and is making the first move). valid ONLY as input.

A instance of `<move>` that conforms to the above shall be called "valid" and one that does not is "invalid". 

A instance of `<move>` is valid AND describes a move allowed by the chess rules as applied to the current gamestate (board) shall be called legal.

## \<time\> - specifications

The symbol `<time>` shall always be the base 10 representation of a integer \\(0 \leq t \leq 1000\\).

## \<status\> - specifications

The symbol `<status>` shall be either:

- The character `A`, indicating your move was accepted by the judge. 
- The character `D`, indicating your move was denied by the judge. 

## \<state\> - specifications 

The symbol `<state>` shall be a FEN representation of the current board state. 
