ALL: 01_whatIsEcology/notes.pdf 01_whatIsEcology/notes.html 01_whatIsEcology/presentation.html \
		 01_whatIsEcology/Rcode.pdf 01_whatIsEcology/Rcode.html 02_lifeEnviron/presentation.html \
		 03_popDynamics/notes.pdf 03_popDynamics/notes.html 03_popDynamics/Rcode.html 03_popDynamics/presentation.html \
		 04_behavior/notes.pdf 04_behavior/notes.html 04_behavior/Rcode.html 04_behavior/presentation.html \
		 05_metapopulation/notes.pdf 05_metapopulation/notes.html 05_metapopulation/presentation.html \
		 06_niche/notes.pdf 06_niche/notes.html 06_niche/presentation.html

OStype := $(shell uname -s)

ifeq ($(OStype), Linux)
	   view = evince
endif

ifeq ($(OStype), Darwin)
	   view = open
endif

%.pdf: %.Rmd
	Rscript -e 'rmarkdown::render("$<", output_format = "bookdown::pdf_document2")'
	$(view) $@

%.html: %.Rmd
	if [[ $< == *notes* ]]; then Rscript -e 'rmarkdown::render("$<", output_format = "tufte::tufte_html")'; fi
	if [[ $< == *Rcode* || $< == *presentation* ]]; then Rscript -e 'rmarkdown::render("$<")'; fi
	$(view) $@
			
clean:
	rm -fv */*.aux */*.log */*.toc */*.blg */*.bbl */*.synctex.gz
	rm -fv */*.nav */*.aux */*.snm 
	rm -fv */*.out */*.bcf */*blx.bib */*.run.xml
	rm -fv */*.fdb_latexmk */*.fls
