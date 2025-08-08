# List publications by category

Simple Latex code and workflow to list your publications by category

## Description

Academics are often asked to produce lists of their own publications, usually for internal documentation, promotion applications, etc. It's feasible to create these lists manually when you only have a few papers, but as the number grows, this task cries out for automation. There's probably many different ways to do this, but this small repository details the way that I've found works for me.

## Workflow

* First, head to [Scopus](https://www.scopus.com) and find your author profile (it should be automatically created by Scopus). You can then [claim ownership](https://www.elsevier.com/en-gb/products/scopus/author-profiles) of it.
* Once this is working, you should see a fairly accurate list of your publications. Login, then choose 'export all' and download a BibTex file of all your papers. Probably the default citation information is fine (but adjust as necessary).
* If necessary, edit the BibTex file - for example, if you only need to show publications from certain years. The easiest way to do this is with a tool such as [BibDesk](https://bibdesk.sourceforge.io/), which comes with the default Mac LaTex install.
* Use the LaTex code in this repository (`main.tex`) to generate your publications list (e.g. on overleaf, or whatever install you like). Make sure you name the bib file correctly in the line `\addbibresource{scopus.bib}`. That's it! An example scopus file and pdf is in this repository.

## How it works

The key here is to set up biblatex correctly via the command `\usepackage[sorting=ydnt, style=ieee, url=false, maxbibnames=50, backend=biber,defernumbers]{biblatex}` - these options can be changed depending on what you need. See [biblatex documentation](https://www.overleaf.com/learn/latex/Articles/Getting_started_with_BibLaTeX) for more info. 

In my particular case I wanted everything listed within each category by inverse date (newest first, hence the `sorting=ydnt` command). I also wanted entries to be numbered (`style=ieee`) uniquely (`defernumbers`), and for papers with many authors not to display all authors (`maxbibnames=50`).

The commands `\printbibliography[type={article},title={Journal Articles},notkeyword={other},notkeyword={patent}]` etc. are used to downselect entries within each section by category. It's a bit cumbersome but it works.



