# Basic makefile for latex document
# Author: Ivan Moreno
# Sep	2020

PDF_TEX = pdflatex -interaction=nonstopmode
PDF_VIEWER = okular
DATE=$(shell TZ=America/Mexico_City date +%F)

.DEFAULT_GOAL := all

# remove all auxiliar files
.PHONY: clean 
clean:
	@echo "Removing auxiliar files"
	@find ./ -maxdepth 1 ! -name "cv_en.tex" \
		-name "cv_e*" -type f -printf "Removing %P\n" -delete

# generate final document
all: cv_en.pdf

en: cv_en.pdf
	@echo "Compiling english version"

# generate pdfs
cv_en.pdf: cv_en.tex
	$(PDF_TEX) cv_en.tex

# open the document
view: cv_en.pdf
	@echo "Opening with ${PDF_VIEWER}..."
	@exec $(PDF_VIEWER) cv_en.pdf &> /dev/null &

view-en: cv_en.pdf
	@echo "Opening cv_en.pdf with ${PDF_VIEWER}..."
	@exec $(PDF_VIEWER) cv_en.pdf &> /dev/null &

patch-date: cv_en.tex
	@echo "Add timestamp..."
	sed -i "s|last-update-year-month-day|${DATE}|g" cv_en.tex