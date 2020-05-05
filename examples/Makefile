.PHONY: MyDoc.pdf all clean

TEXS=$(wildcard letter*.tex)

all: $(TEXS:.tex=.pdf)

%.pdf: %.tex rawLetter.tex
	@env TEXINPUTS=../:: latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode" -use-make $<
	@env TEXINPUTS=../:: latexmk -c $^

clean:
	@env TEXINPUTS=../:: latexmk -CA
