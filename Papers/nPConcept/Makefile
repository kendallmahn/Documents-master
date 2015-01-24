TEX = pdflatex
BIB = bibtex
#main file
texfile = NuPrismPaper
FIGS=$(wildcard figures/*.*)
#all texfiles
SECS=$(wildcard *.tex)

REVTEX:=$(CURDIR)/revtex4-1/tex/latex/revtex
REVBST:=$(CURDIR)/revtex4-1/bibtex/bst/revtex
NATBIB:=$(CURDIR)/natbib

export TEXINPUTS:=$(CURDIR):$(REVTEX):$(TEXINPUTS)
export BSTINPUTS:=$(CURDIR):$(REVBST):$(BSTINPUTS)


.PHONY: pdf
.PHONY: clean

all: pdf

pdf: $(texfile).pdf

$(texfile).pdf : $(SECS) $(FIGS) $(texfile).bib
	$(TEX) $(texfile)
	$(BIB) $(texfile)
	$(TEX) $(texfile)
	$(TEX) $(texfile)
	open $(texfile).pdf

clean:
	@ls $(texfile).* | grep -v '.tex\|.bib' | xargs -I {} rm {}

revtex: 
	mktexlsr $(PWD)/revtex4-1

natbib: $(NATBIB)/natbib.sty

$(NATBIB)/natbib.sty:
	rm natbib.sty; cd $(NATBIB); ls; latex natbib.ins; cd ../; ln -s $(NATBIB)/natbib.sty .

