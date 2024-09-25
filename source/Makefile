XSLTPROC = /usr/bin/xsltproc
XMLLINT = /usr/bin/xmllint
MKDIR = mkdir -p
SHELL = /bin/bash

BUILD_DIR = ../build

HTML_CHUNK_DIR = $(BUILD_DIR)/html-chunk
HTML_CHUNK_TARGET = $(HTML_CHUNK_DIR)/index.html
HTML_XSLTPROC_OPTS = --xinclude

# src
SOURCE_DIR = .

VERSION = 1.2
VERSION_SCRIPT = $(SOURCE_DIR)/version.sh
VERSION_SOURCE = $(SOURCE_DIR)/version.xml

XML_SOURCE = $(SOURCE_DIR)/book.xml
XSL_DIR = $(SOURCE_DIR)/stylesheets

.PHONY: all clean html-chunk valid

all: html-chunk

clean:
	@rm -f $(HTML_CHUNK_TARGET)

html-chunk: valid $(HTML_CHUNK_TARGET)

$(HTML_CHUNK_TARGET): $(XML_SOURCE)
	$(XSLTPROC) $(HTML_XSLTPROC_OPTS) --output $(HTML_CHUNK_DIR)/ $(XSL_DIR)/xhtml-chunk.xsl $(XML_SOURCE)

valid: $(VERSION_SOURCE)
	$(XMLLINT) --xinclude --noout --nonet --postvalid $(XML_SOURCE)

$(VERSION_SOURCE): version

version:
	@$(SHELL) $(VERSION_SCRIPT) $(VERSION) > $(VERSION_SOURCE).tmp
	@if cmp -s $(VERSION_SOURCE) $(VERSION_SOURCE).tmp; then \
	  rm $(VERSION_SOURCE).tmp; \
	else \
	  mv $(VERSION_SOURCE).tmp $(VERSION_SOURCE); \
	fi
