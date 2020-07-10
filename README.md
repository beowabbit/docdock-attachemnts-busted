# docdock-attachments-busted

This repository demonstrates that the `attachments`, `children`,
and `expand` shortcodes in DocDock are busted under Hugo 0.73, which
defaults to the "Goldmark" markdown library while they work under 0.48
which defaulted to "Black Friday".

Under 0.48, attachments render as documented, with an "Attachments"
header with paperclip icon and a list of links to attachments in the
locations indicated by the documentation.  (The style doesn't match
other lists in DocDock, but that's always been the case.)

Under 0.73, the HTML for the list is output, but as preformatted text,
as if the HTML were being quoted, and with no header.

To reproduce, after cloning this repo, cd into it and run

    git submodule update --init

Run "hugo server" with an 0.73 version of Hugo (which you can get
from https://github.com/gohugoio/hugo/releases/tag/v0.73.0),
and you'll see that each page has a broken attachments
section.  Run it with an 0.48 version (which you can get from
https://github.com/gohugoio/hugo/releases/tag/v0.48) and you'll see that
attachments render normally.  For convenience I've included Linux 64-bit
Hugo binaries for 0.73 and 0.48 in the repo here, so you can just do

    ./hugo-v0.48 server

and

    ./hugo-v0.73.0 server

if you're on Linux 64-bit and you're willing to run random binaries some
dude on the Interwebs sends you.

Since this is a Goldmark vs. Black Friday issue, it can be tested just
with recent Hugo; uncomment the two lines forcing Black Friday rendering
from `config.toml` (or `cp config.toml-blackfriday config.toml`) and run
`hugo server`.

0.48 happened to be the version that we were trying to upgrade from when
we discovered this problem, but probably any version prior to 0.60 will
default to Black Friday rendering and work fine.

The documentation seems to be inconsistent about whether I need a closing
slash before the `}}` of the `attachments` shorcode, but omitting it
doesn't seem to make a difference.)

(I created a demo with a regular leaf pages `content/animals/insects.md`
and `content/animals/mammals.md`, with leaf bundle `content/plants/index.md`,
and with branch bundles `content/animals/_index.md` and `content/_index.md`,
because some closed issues seemed to suggest they were handled
differently.  All work fine under 0.48.)

