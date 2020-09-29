# Basic makefile for latex document
# Author: Ivan Moreno
# Sep	2020

PDF_TEX = pdflatex -interaction=nonstopmode
PDF_VIEWER = okular

.DEFAULT_GOAL := all

# remove all auxiliar files
.PHONY: clean 
clean:
	@echo "Removing auxiliar files"
	@find ./ -maxdepth 1 ! -name "cv_en.tex" ! -name "cv_es.tex" -name "cv_e*" -type f -exec rm -v {} \;

# generate final document
all: cv_en.pdf cv_es.pdf

en: cv_en.pdf
	@echo "Compiling english version"

es: cv_es.pdf
	@echo "Compiling spanish version"

# generate pdfs
cv_en.pdf: cv_en.tex
	$(PDF_TEX) cv_en.tex

cv_es.pdf: cv_es.tex
	$(PDF_TEX) cv_es.tex

# open the document
view: cv_en.pdf cv_es.pdf
	@echo "Opening with ${PDF_VIEWER}..."
	@exec $(PDF_VIEWER) cv_es.pdf cv_en.pdf &> /dev/null &

view-en: cv_en.pdf
	@echo "Opening cv_en.pdf with ${PDF_VIEWER}..."
	@exec $(PDF_VIEWER) cv_en.pdf &> /dev/null &

view-es: cv_es.pdf
	@echo "Opening cv_es.pd fwith ${PDF_VIEWER}..."
	@exec $(PDF_VIEWER) cv_es.pdf &> /dev/null &

#compress: cv_en.pdf cv_es.pdf
#	@echo "Compress pdf file -> ${TARGET}-compressed.pdf"
#	@gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dNOPAUSE -dQUIET -dBATCH -dPrinted=false -sOutputFile=$(TARGET)-compressed.pdf $(TARGET).pdf
