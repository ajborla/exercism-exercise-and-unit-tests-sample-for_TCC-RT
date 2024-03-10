# exercism-exercise-and-unit-tests-sample-for_TCC-RT
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
The unit test library, unit tests, and Exercism exercises, are all resident in the current repository, and require no installation.

_TCC-RT_ is a proprietary Windows application (although previous incarnations have targeted older platforms like _DOS_ and _OS/2_). As such, there is no source code, nor ZIP file, available. It is solely installable by downloading the version-relevant installer file, and executing it, a painless, straightforward, and generally reliable process.

Here is the official download page: [Take Command Downloads](https://jpsoft.com/all-downloads/all-downloads.html)

Persusing this page reveals the availability of several products, as well as **all** versions of those products. To avoid confusion, the download of [TCC-RT 25.0](https://jpsoft.com/downloads/v25/tcc-rt.exe), the version used for testing the current repository, is recommended.

The installer will have been placed into the downloads directory, generally `%HOMEDRIVE%%HOMEPATH%\Downloads`, although this may vary depending on your personal configuration. Regardless, `tcc-rt.exe` is the installer, and needs to be executed to effect installation.

Once installed, the application is located in the `"%ProgramFiles%"\JPSoft\TCC_RT_25\` directory, and, if desired, may be added to the `PATH` environment variable.

Assuming a _Command Prompt_ window has been opened, then a `Hello, World!` string appearing on the console after issuing the following command:

```plain
"%ProgramFiles%"\JPSoft\TCC_RT_25\tcc.exe /A /D /I /Q echo Hello, World!
```

or, if `PATH` has been updated:

```plain
tcc.exe /A /D /I /Q echo Hello, World!
```

is indicative of a successful installation.

Despite _TCC-RT_ being a Windows application it should be possible to use it in a *NIX / Linux environment (real or emulated).

It _has been_ tested under _Git for Windows_ (no additional installation or configuration required), where the equivalent to the earlier-issued command is:

```plain
/c/'Program Files'/JPSoft/TCC_RT_25/tcc.exe -A -D -I -Q echo Hello, World!
```

It should also be possible to execute it on a native *NIX / Linux using [Wine](https://www.winehq.org/). This capability, however, has not been tested.

## Usage
Assuming a _Command Prompt_ window has been opened,
and that the current directory points to a clone of this repository, the unit tests for an exercise, for example, the `leap` exercise, may be effected by invoking the `leap-test` script, like so:

```plain
"%ProgramFiles%"\JPSoft\TCC_RT_25\tcc.exe /A /D /I /Q leap-test.btm
```

A successful execution will see generation of the following output:

```plain
OK - "Year not divisible by 4: common year"
OK - "Year divisible by 2, not divisible by 4 in common year"
OK - "Year divisible by 4, not divisible by 100: leap year"
OK - "Year divisible by 4 and 5 is still a leap year"
OK - "Year divisible by 100, not divisible by 400: common year"
OK - "Year divisible by 100 but not by 3 is still not a leap year"
OK - "Year divisible by 400: leap year"
OK - "Year divisible by 400 but not by 125 is still a leap year"
OK - "Year divisible by 200, not divisible by 400 in common year"
OK - "No input should return an error"
OK - "Too many arguments should return an error"
OK - "Float number input should return an error"
OK - "Alpha input should return an error"
```

Continuing the current example, `leap.btm`, is the exercise file, and `leap-test.btm` is the test file, both containing TCC language code. The latter is structured as follows:

```plain
@echo off
call TCCUNIT << "EOF"
"Year not divisible by 4: common year" EQ 0 false leap 2015
"Year divisible by 2, not divisible by 4 in common year" EQ 0 false leap 1970
"Year divisible by 4, not divisible by 100: leap year" EQ 0 true leap 1996
"Year divisible by 4 and 5 is still a leap year" EQ 0 true leap 1960
"Year divisible by 100, not divisible by 400: common year" EQ 0 false leap 2100
"Year divisible by 100 but not by 3 is still not a leap year" EQ 0 false leap 1900
"Year divisible by 400: leap year" EQ 0 true leap 2000
"Year divisible by 400 but not by 125 is still a leap year" EQ 0 true leap 2400
"Year divisible by 200, not divisible by 400 in common year" EQ 0 false leap 1800
"No input should return an error" EQ 1 "ERROR: Invalid arguments. USAGE: leap year" leap
"Too many arguments should return an error" EQ 1 "ERROR: Invalid arguments. USAGE: leap year" leap 2016 4562 4566
"Float number input should return an error" EQ 1 "ERROR: Only positive values allowed. USAGE: leap year" leap 2016.54
"Alpha input should return an error" EQ 1 "ERROR: Only positive values allowed. USAGE: leap year" leap "abcd"
EOF
```

It comprises a HEREDOC in which each line contains the test parameters of a unit test, and is fed to the `TCCUNIT.btm` script where each unit test is executed.

Note that tests may be commented out (using **_#_** at the start of a HEREDOC line), modified, and new tests added. Note this character is not the language's comment delimiter (the double colon, **_::_**, serves this purpose), merely an arbitrary character chosen for convenience.

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

