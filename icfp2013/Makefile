# slick Makefile template for use with texd, etc...

.SUFFIXES: .dvi .ps

# new-style pattern-matching, enables multiple dependencies.
%.dvi: %.tex $(SRCS) $(FIGURES)
	latex $<

# old-style pattern-matching is good enough here.
.dvi.ps:
	dvips $*.dvi

# name of file to be latexed
TARGET = interop

# define SRCS, FIGURES, BIBS, whatever other lists of files you want to add. 
SRCS = sigplanconf.cls

# this is my big bib file, you can add other files as well, 
# but they must be listed in your \bibliography{...} directive.
# Listing them here means that make will rerun bib every time you update 
# one of the bib files.  This is usually a good idea.
#BIBS = /home/wand/refs.bib
#BIBS = bibliography.bib

# uncomment "bib" to run bibtex as well.
preview: latest.ps $(SRCS) $(FIGURES) # bib

latest.ps: $(TARGET).ps
	cp $(TARGET).ps latest.ps

bib: $(TARGET).bbl

$(TARGET).dvi: $(TARGET).tex $(SRCS) $(FIGURES) Makefile
	time latex $(TARGET)

$(TARGET).bbl: $(TARGET).aux $(BIBS)
	bibtex $(TARGET)
