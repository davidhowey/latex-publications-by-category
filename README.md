# List publications by category

Simple Latex code and workflow to list your publications by category

## Description

Academics are often asked to produce lists of their own publications, usually for internal documentation, promotion applications, etc. It's feasible to create these lists manually when you only have a few papers, but as the number grows, this task cries out for automation. There's probably many different ways to do this, but this small repository details the way that I've found works for me.

## Workflow

* First, head to [Scopus](https://www.scopus.com) and find your author profile (it should be automatically created by Scopus). You can then [claim ownership](https://www.elsevier.com/en-gb/products/scopus/author-profiles) of it.
* Once this is working, you should see a fairly accurate list of your publications. Login, then choose 'export all' and download a BibTex file of all your papers. Probably the default citation information is fine (but adjust as necessary).
* If necessary, edit the BibTex file - for example, if you only need to show publications from certain years. The easiest way to do this is with a tool such as [BibDesk](https://bibdesk.sourceforge.io/), which comes with the default Mac LaTex install.
* Use the LaTex code in this repository to format your publications list (e.g. on overleaf, or whatever install you like). The key is to set up biblatex correctly via a command such as `\usepackage[sorting=ydnt, style=ieee, url=false, maxbibnames=50, backend=biber,defernumbers]{biblatex}` - these options can be changed depending on what you need. See [biblatex documentation](https://www.overleaf.com/learn/latex/Articles/Getting_started_with_BibLaTeX) for more info.



