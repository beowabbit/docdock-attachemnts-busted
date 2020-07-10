# docdock-attachments-busted

This repository demonstrates that the `attachments` shortcode in DocDock is busted under Hugo 0.73, while it
works under 0.48.

Under 0.48, attachments render as documented, with an "Attachments"
header with paperclip icon and a list of links to attachments in the
locations indicated by the documentation.  (The style doesn't match
other lists in DocDock, but that's always been the case.)

Under 0.73, the HTML for the list is output, but as preformatted text,
as if the HTML were being quoted, and with no header.

To reproduce, after cloning this repo, cd into it and run

    git submodule update --init

