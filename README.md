# You Don't Need Vi/Vim!

ed(1) is the standard editor.

## Purpose

This repo serves to help me do things in ed(1) that I'd previously rely on vi(1)/vim(1) for. 

### Because... reasons

In a world with so much software bloat, there needs to be a hero. Hello, ed(1)!

I love Vim, but not everyone has 8MB RAM free to edit a simple text file, especially if they've opened a modern web browser.

ed(1) has been around since 1969 - when computing resources were tight and efficient editing was essential. 

Many of us have access to powerful computers and internet that allows for walls of text to be quickly loaded onto the screen. ed(1) can run on the slowest of remote connections and consume minimal system resources. 

I'd like to be able to work quickly on any system, including low-spec hardware and poor internet connections.

Part insanity, part idealism, I want to show the world that you don't need an expensive MacBook to get sh*t done. I want to show what any used or cheap computer can do with the power of solid, open source tools that have been around for 50 years.

## You don't need vi/vim to:

### Globally change simple text in a file
A test you can easily do in `sed` or other tools, but if you're already in your editor and want to change a variable name throughout the file, for example, you'll see the similarities between `ed(1)`, `sed(1)` and `vi(1)` - wonder why that is...?

#### Vim

 - `:%s/foo/bar/g`

#### ed

 - `1,$s/foo/bar/g`

For lines number 1, through last line (`$`), substitute (`s`) all occurrances (`g`) of `foo` with `bar`.

### Print all function names with line numbers

Useful for files with (probably too) many functions. While a bloated IDE may steal your pixels with a permanent preview of the file structure, how often do you use it?

#### Vim

 - `:g/function /p`

Assuming you have line numbers showing already, else, turn them on with `:set nu`.

#### ed

 - `g/function /n`

Defaults to range of `(1,$)` (all lines), `g` applies the given commands each line matching the regular expression. From `man ed`: `(1,$)g/re/command-list`. What makes you smile: `g/re/p` to print matches! Is it a conspiracy, or is `ed(1)` the Illuminati of all UNIX commands?!?

### Change text inside quotes

These kind of change inside, change around commands are something I use a lot of in Vim for web development, support for change inside tags, especially.

#### Vim

 - `ci"`
 - `the new text`
 - `Esc`

#### ed

 - `,s/".*"/"the new text"/`
 - `Return`

These examples both work well when there is only one instance of quoted text on the current line. When there are multiple instances on the same line, using the example Vim command will edit just the first instance. Using the ed command will have undesired effects and require more thought into the matching pattern if you want to edit just the first instance.


### Jump to end of function definition

#### Vim

 - `/function foo`
 - `Return`
 - `$%`

#### ed

 - `/function foo`
 - `Return`
 - `;/^    }`
 - `Return`

This version in `ed(1)` needs some improvement. It currently requires that you know the number of spaces/tabs your closing curly brace will be on. This should give me a good start on figuring out how to print/cut/indent whole function definitions.

### Print a whole function definition

#### Vim

 - TBC

#### ed

 - `g/function foo/ka`
 - `Return`
 - `;/^    }`
 - `Return`
 - `'a,.n`

Expecting only one match for our function definition, we can use a global search, which will return the line number, as opposed to just a search with `/`. We mark this as position `a` with the `k` command, for later use. We then find the end of the function definition. Now, we can print from the start of the function, marked with `a`, through the end (our current line, `.`).

## Further (ed)ucation

 - `man ed`
 - Read the source code. If you've checkout out the AnonCVS repo for OpenBSD (you are using OpenBSD, right?), simply `ed /usr/src/bin/ed/main.c` and see what the `-x` flag used to do!
 - Get Michael W Lucas' [Ed Mastery](https://mwl.io/nonfiction/tools) book. The best (and only?) book on `ed(1)`. It costs less than the patience required to edit large files in `ed(1)`.

