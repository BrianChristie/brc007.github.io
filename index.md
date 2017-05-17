# Writing a Thesis with LaTeX in 2017
Recently I typeset an academic thesis in LaTeX. Because LaTeX is so old, a ton of the advice online is conflicting or outdated. Here’s my notes on what worked well in May 2017.
I highly recommend the excellent [ShareLaTeX documentation pages](https://www.sharelatex.com/learn) to get started. Also the [LaTeX WikiBook](https://en.wikibooks.org/wiki/LaTeX) is very helpful.

Before starting, ask around in your department to see if anyone has a LaTeX file that’s already setup to meet the requirements of your graduate college. If there isn’t one then you’ll have to start from scratch.

## Base Document Class
The first thing to decide is what document class to use. In 2017 there’s two main choices, [Memoir](http://ctan.org/pkg/memoir) and [KOMA-script](http://ctan.org/pkg/koma-script). Here’s a StackExchange question on [What are the strengths and weaknesses of KOMA-Script and memoir?](https://tex.stackexchange.com/questions/7742/what-are-the-strengths-and-weaknesses-of-koma-script-and-memoir?lq=1). I used Memoir as I found it had somewhat better documentation. You could also choose to use a base LaTeX class such as book, and find a package for every single feature you need.

## Packages
A major issue with using LaTeX in 2017 is that for every single thing you want to do, there will be a minimum of 2 or 3 packages that could work, and it’s very difficult to determine which one is the “right one”. When you’re just trying to get something typeset researching this can be excruciating. 

Before you start, take a look at what packages are automatically included and emulated by Memoir (section 18.24 in the [Memoir Manual](http://texdoc.net/texmf-dist/doc/latex/memoir/memman.pdf)

Here’s my recommendations on what to use together with the functionality included in Memoir:
- For drawing charts and graphs, use [Pgfplots](https://www.sharelatex.com/learn/Pgfplots_package) and [TikZ](https://www.sharelatex.com/learn/TikZ_package)
- For pretty tables use Booktabs.  Look at the first few pages of the [BookTabs Manual](http://mirror.ibcp.fr/pub/CTAN/macros/latex/contrib/booktabs/booktabs.pdf)
- For tables that span across pages use [LongTable](https://www.sharelatex.com/learn/Tables#/Multi-page_tables)
- To rotate pages for landscape tables use [pdflscape](https://www.ctan.org/pkg/pdflscape?lang=en). 
	- This can be used together with LongTable and double sided printing to get a table that is read top to bottom across two pages.
- To change the page margins to a specific size to conform to university regulations, or to make a long landscape oriented table look nice, use [Geometry](https://www.sharelatex.com/learn/Page_size_and_margins). 
- A major issue can be getting figures to appear where you want them, because LaTeX floats them to a nearby spot where their size fits best with the surrounding text. To override this as needed, use [float](https://en.wikibooks.org/wiki/LaTeX/Floats,_Figures_and_Captions) and the H option on your figures. Memoir’s implementation makes H do nothing and it will drive you crazy until you figure this out.
- For figures you also may want [flafter](https://tex.stackexchange.com/questions/15706/force-floats-to-be-typeset-after-their-occurrence-in-the-source-text) to force floats to be typeset after their occurrence in the document (and not to float above).
- To insert an existing PDF as an appendix use [pdfpages](https://www.ctan.org/pkg/pdfpages?lang=en)
- To get your PDF file metadata such as Table of Contents and Author Name working properly use [hyperref](https://en.wikibooks.org/wiki/LaTeX/Hyperlinks)

## Languages other than English
I used babel together with XeLaTex to get UTF-8 unicode characters working. XeLaTeX is unicode aware so this should work properly without having to use inputenc. 