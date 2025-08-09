# List publications by category

Simple Latex code and workflow to list your publications by category, cleanly presented and numbered

## Description

Academics are often asked to produce lists of their own publications, usually for internal documentation, promotion applications, etc. It's feasible to create these lists manually when you only have a few papers, but as the number grows, this task cries out for automation. There's probably many different ways to do this, but this small repository details the way that I've found works for me.

## Prerequisites

A basic familiarity with LaTex and BibTex is assumed here, as well as a way to compile LaTex documents (e.g., [Overleaf](https://www.overleaf.com), or a local install on your computer). If you are new to LaTex there are many online resources you can use to get started, such as [this one](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes).

## Workflow

* First, head to [Scopus](https://www.scopus.com) and find your author profile (it should be automatically created by Scopus). You can then [claim ownership](https://www.elsevier.com/en-gb/products/scopus/author-profiles) of it.
* Once this is working, you should see a fairly accurate list of your publications. Login, then choose 'export all' and download a BibTex file of all your papers. Probably the default information is fine (but adjust as you want).
* Edit the BibTex file to remove any junk that scopus puts at the top, or resolve errors such as spaces in the keys that refer to each bib item. If you want, further edit the BibTex file to your needs - for example, if you only need to show publications from certain time periods. The easiest way to do checking and editing is with a tool such as [BibDesk](https://bibdesk.sourceforge.io/), which comes with the default Mac LaTex install (or JabRef, Zotero, etc.). BibDesk will also show duplicate keys entries, general issues with the bib file etc.
* Get rid of any unicode gremlins in the bib file (thanks, scopus, grrr). A quick way to do this is to search for this regular expression in VSCode: `[^\x00-\x7f]`.
* To show conference abstracts separately, add an entry to any conference abstract (should bib type be `@inproceedings`) that says `keywords={confabstract}`.
* To show patents separately, add them manually as type `@article` in the `.bib` and include `keywords={patent}` in each.
* For any other types of documents (e.g., opinion pieces, etc.) add them manually as `@article` in the `.bib` and include `keywords={other}` in each.
* Use the LaTex code in this repository (`main.tex`) to compile your publications list (e.g. on overleaf, or whatever install you like). Make sure you name the `.bib` file correctly in the line `\addbibresource{scopus.bib}`. That's it! An example `.bib` file and `.pdf` file with some of my papers are in this repository.
* Check the resulting pdf and modify BibTex entries if necessary (e.g., capitalisation issues). Rinse and repeat!

Once you have a Bib file that works, you could just add newer publications later to it, rather than redoing this entire process every time.

## How it works

The key here is to set up biblatex correctly via the command `\usepackage[sorting=ydnt, style=ieee, url=false, maxbibnames=50, backend=biber,defernumbers]{biblatex}` - these options can be changed depending on what you need. See [biblatex documentation](https://www.overleaf.com/learn/latex/Articles/Getting_started_with_BibLaTeX) for more info. 

In my particular case I wanted everything listed within each category by inverse date (newest first, hence the `sorting=ydnt` command). I also wanted entries to be numbered (`style=ieee`) uniquely (`defernumbers`), and for papers with many authors not to display all authors (`maxbibnames=50`).

The commands `\printbibliography[type={article},title={Journal Articles},notkeyword={other},notkeyword={patent}]` etc. are used to downselect entries within each section by category. It's a bit cumbersome but it works.



