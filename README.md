# You Don't Need Vi/Vim!

ed(1) is the standard editor.

## Purpose

This repo serves to help me do things in ed(1) that I'd previously rely on vi(1)/vim(1) for. 

### Because... reasons

In a world with so much software bloat, there needs to be a hero. Hello, ed(1)!

I love Vim, but not everyone has 8MB RAM free to edit a simple text file, especially if they've opened a modern web browser.

ed(1) has been around since 1969 - when computing resources were tight and efficient editing was essential. 

[A

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
