# SkyBridge certificates

Draws an A4 certificate entirely in code, in Photoshop, from an empty document. Built to issue the first year certificates for the SkyBridge club Python workshop, which came to 84 people across members and external participants.

## The situation

Eighty four certificates, each with a different name, all needing to look identical otherwise. The manual version of this job is opening a design file 84 times, retyping a name, exporting, and getting one of them wrong without noticing. Nobody checks certificate number 61 until the person holding it points at the typo.

## What the script actually does

`build_certificate.jsx` is not a mail merge over a template. It creates a 3508 by 2480 document at 300 dpi and builds the whole poster from nothing: navy background, a radial glow behind the title, scattered glossy 3D Python logos, the typography, the stamp, the accent rules. Every element is placed by code, which is why the layout is reproducible and why changing the accent colour is a one line edit rather than an afternoon.

The palette lives at the top of the file as named constants: navy, cream, python yellow, and the supporting blues. So does the geometry. Nothing is positioned by dragging.

`composition.html` is the layout companion. Iterating on typography and spacing in a browser is much faster than iterating in a PSD, so the composition was settled in HTML first and then translated into the ExtendScript.

## Files

    build_certificate.jsx    the generator, runs inside Photoshop
    composition.html         browser preview used to settle the layout
    assets/                  logos, background plate, colour palette, stamp
    assets/fonts/            Poppins, Anton, Archivo Black, Space Grotesk

## Running it

Set the two path constants near the top of `build_certificate.jsx`, `ASSETS` and `OUT`, to wherever you have put this folder. Then in Photoshop go to File, Scripts, Browse, and select the script.

## What I would do differently

ExtendScript is the right tool for reaching into Photoshop and a dead end of a language everywhere else. Debugging it is unpleasant and it has no real error reporting, which is why the script carries its own logging array. If the visual design had been simpler I would have generated the whole thing from HTML and printed to PDF, which is the direction `composition.html` was originally heading.
