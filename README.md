# exercism-exercise-and-unit-test-sample-for_TCC-RT
> Sample exercises, unit tests, and test library, for proposed Exercism track, TCC-RT

|||
| :---     | :--- |
| author:  | Anthony J. Borla |
| contact: | [ajborla@bigpond.com](ajborla@bigpond.com) |
| license: | MIT |

## Overview

### Product / Language
[_Take Command Console_](https://en.wikipedia.org/wiki/Take_Command_Console) (or [_TCC_](https://en.wikipedia.org/wiki/Take_Command_Console)), is a Windows-based command-line interpreter(CLI) that is upwardly compatible with the default CLI for that platform, [_CMD_](https://en.wikipedia.org/wiki/Cmd.exe), and intended as a more feature-rich replacement for it. It is proprietary software that is still actively developed, and marketed by, [_JP Software_](https://jpsoft.com/).

In 2016 _JP Software_ made [_TCC-RT_](https://jpsoft.com/blogs/releases/tcc-rt-released.html), the _TCC_-Runtime, freely available, with the express intention of allowing end users to execute, **_royalty-free_**, non-interactive scripts:

> Obviously there is some risk here for JP in that we may lose some Take Command sales. Hopefully the end result will be a wider dissemination of TCC scripts and general familiarity with Take Command.

Use of _TCC-RT_ in a non-commercial, educational setting, such as in an Exercism track, would appear to dovetail with this expressed hope.

The TCC command language may be described as a superset of the [_CMD_](https://en.wikipedia.org/wiki/Cmd.exe) language, and is capable of executing such command files without modification.

It does, however, also extend the language to include additional commands, control structures, and capabilities such as floating point and datetime arithmetic, as well as the ability to implement user-defined functions, bringing it closer to being a true scripting language.

The prime reference and learning resource for the language is the [TCC Reference Manual](https://jpsoft.com/downloads/v31/TakeCommand.pdf).

An interesting resource (well worth exploring), actually for an older incarnation of _TCC_, is: [4DOS Info](https://4dos.info/).

### Test Library
The author was unable to source an _official_, let alone, _any_, unit test framework, therefore proceeded to implement a simple test library.

The result is, `TCCUNIT.btm`, and comprises approximately 29 lines of code, spread over two subroutines.

It is functional, insofar as it successfully tests all twenty one of the included exercises. Planned extensions (contingent on acceptance of _TCC-RT_ as an Exercism track) include:
* Emit TAP-compliant output
* Emit Exercism spec-compliant JSON output

## Installation
## Usage

## Acknowledgements
The author frequently referred to, and adapted, the unit tests in the [Exercism Bash Track](https://exercism.org/tracks/bash). Many thanks to the authors of those tests for their work, particularly, the clarity of test names, and the addition of extra tests.

Thanks to JPSoftware for making [_TCC-RT_](https://jpsoft.com/downloads/v25/tcc-rt.exe) freely available, so enabling learners around the world to experience the power of this command language via a learning resource such as a _TCC-RT_-based Exercism track.

Many thanks, also, to Rex C. Conn, and to Tom Rawson, for authoring [_4DOS_](https://en.wikipedia.org/wiki/4DOS) back in 1989, so commencing the journey that has led to today's [_TCC_](https://en.wikipedia.org/wiki/Take_Command_Console) and _TCC-RT_.

## TODO
Assuming acceptance of this proposal, commence working on the newly-created repositories:

`https://github.com/exercism/tccrt`

and:

`https://github.com/exercism/tccrt-test-runner`

The author expects to effect the transference of current repository contents to the new track.

However, should there be interest, welcomes contributions in the form of new exercises. These should be quite straightforward to implement since committed exercises may be used as templates.

