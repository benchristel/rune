# Rune

Rune is a text editor for the MOSS operating system. It is
inspired by Vim and Kakoune, but has its own idea of how to
do things.

It ships with MOSS.

## Running

Editing a file in MOSS will automatically run Rune.

## In-editor help

The first thing you probably want to know is how you're
going to remember all the stuff in this document! After you
use Rune for a while, these commands will be second nature,
but until then, you can get in-editor help by pressing the
? or / key. Note that if you are in **insert mode** (see
below), pressing this key will simply insert a ? or /
character, and you will have to leave insert mode to see
the help screen.

## General Concepts

Rune treats text documents as simple lists of characters—
just one byte after another. A document loaded into Rune's
memory (or created there) is called the **buffer**.

Rune has a concept of a **selection**, which is a slice of
the buffer. A selection has two ends, the **anchor** and the
**cursor**. The cursor is the end that moves around when you
issue movement commands. The anchor stays put. The anchor
and cursor both represent positions in between characters.

The selection is often an empty slice, in which case the
anchor and cursor are at the same position.

## Movement commands

### Grid movement

The h, j, k, and l keys move as in Vim. m is an alias for h.
These keys move the cursor and then move the anchor to the
cursor's new position, effectively deselecting any text that
was selected before the move.

Holding shift while pressing the movement keys, to get H, J,
K, L, M, causes the cursor to move while the anchor stays
put, effectively expanding or contracting the selection by
one character or line.

### Word movement

The w and e keys move word-by-word. e moves forward to the
end of the next whitespace-separated word, while w
moves back to the beginning of the previous whitespace-
separated word.

As with other movement keys, holding shift while moving
word-by-word expands or contracts the selection.

### Line movement

g goes to the end of the current line; a goes to the
beginning. Shift-g and shift-a select.

### Search movement

f and t work as in Vim. shift-F and shift-T select in
addition to moving.

s works like Vim's /.

## Editing Text

Pressing i goes into **insert mode**. While in insert mode,
all keys simply insert characters into the buffer before the
current selection. If the selection is not empty when you
enter insert mode, the selected text is deleted and moved
to the **kill ring**.

To get out of insert mode, press the semicolon (;) key.
This does not immediately leave insert mode. It merely
displays a banner with the word "Semicolon" at the bottom
of the screen. At this point, if you type a space, newline,
or semicolon, you will remain in insert mode and a literal
semicolon will be inserted. If you press delete, the
"Semicolon" banner disappears—it's as if you never pressed
the semicolon key in the first place. If you press any other
key, you will leave insert mode and no semicolon will be
inserted.

## Copying, cutting, and pasting

You can copy the selected text by pressing c.

v brings up the **paste menu**, which shows all the snippets
that have been copied to the kill ring. The kill ring is
stored on disk, so if you copy in one buffer you can paste
in another. Rune remembers your copy history even after you
reboot the computer!

If you're sure of what you last copied, shift-V simply
pastes the most recent item from the history.

## Key Differences from Vim

There is no separate visual mode—to select text, you hold
`shift` while pressing movement keys.

The w and e keys work a bit differently from Vim's
word-movement keys.

To get out of insert mode, you press semicolon rather than
escape.
