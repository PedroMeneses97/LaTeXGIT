TEXINPUTS := .:$(CURDIR)/include:${TEXINPUTS}
export TEXINPUTS

MAIN = relatorio
RUBBER_OPTS = -d

all: *.tex
	@if [ -x /usr/bin/rubber ]; then rubber $(RUBBER_OPTS) $(MAIN); else pdflatex -interaction=batchmode $(MAIN) && pdflatex -interaction=batchmode $(MAIN); fi
	@gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dNOPAUSE -dQUIET -dBATCH -sOutputFile=compress.pdf relatorio.pdf && mv compress.pdf relatorio.pdf

clean:
	@rm -f *.aux *.log *.toc *.lof *.out *.lot

dist-clean: clean
	@rm -f $(MAIN).pdf

TEXFILES := $(shell find -type f -iname \*.tex)
spell:
	@for i in $(TEXFILES); do \
		aspell -c --encoding="iso8859-1" --lang=pt -t $$i; \
	done

