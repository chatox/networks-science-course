
all: pdf/*.pdf

pdf/%.pdf: odp/%.odp
	soffice --headless --convert-to pdf $<
	mv -f *.pdf pdf/
