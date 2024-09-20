XSLTPROC = /usr/bin/xsltproc
XMLLINT = /usr/bin/xmllint
MKDIR = mkdir -p
SHELL = /bin/bash

XML_SOURCE = ./book.xml

BUILD_DIR = ../build

HTML_CHUNK_DIR = $(BUILD_DIR)/html-chunk
HTML_CHUNK_TARGET = $(HTML_CHUNK_DIR)/index.html
HTML_XSLTPROC_OPTS = --xinclude

XSL_DIR = ./stylesheets

.PHONY: all clean html-chunk valid

all: html-chunk

clean:
	@rm -f $(HTML_CHUNK_TARGET)

html-chunk: valid $(HTML_CHUNK_TARGET)

$(HTML_CHUNK_TARGET): $(XML_SOURCE)
	$(XSLTPROC) $(HTML_XSLTPROC_OPTS) --output $(HTML_CHUNK_DIR)/ $(XSL_DIR)/xhtml-chunk.xsl $(XML_SOURCE)

valid: $(XML_SOURCE)
	$(XMLLINT) --xinclude --noout --nonet --postvalid $(XML_SOURCE)
