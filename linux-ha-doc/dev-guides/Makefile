#
#
#

SRCFILE=ra-dev-guide.asc

PROXY ?= $(shell echo ${http_proxy} | cut -d '/' -f 3 )

# make sure that you have correctly configured ~/.blogpost
BLOGPOST=blogpost.py
# -u unpublish / -U publish
BLOGPOST_OPTS=--force -u --proxy=$(PROXY)
#BLOGPOST_OPTS=--force -U --proxy=$(PROXY)

# Sample customization to enable icons on Wordpress
#   icons must be uploaded to the wordpress web server with the iconsdir path
# It is disabled for this document to avoid additional license and credit attribution
#ASCIIDOC_OPTS=-a icons -a iconsdir=/usr/share/asciidoc/images/icons -f ./wordpress-icons.conf
#ASCIIDOC_OPTS=-a icons -a iconsdir=/images/icons -f ./wordpress-icons.conf
#ASCIIDOC_OPTS2=--asciidoc-opt="-a icons" --asciidoc-opt="-a iconsdir=/images/icons" --asciidoc-opt="-f ./wordpress-icons.conf"

all:
	@echo make html
	@echo make post

html:
	asciidoc $(ASCIIDOC_OPTS) $(SRCFILE)

wp:
	asciidoc -v $(ASCIIDOC_OPTS) -b wordpress $(SRCFILE)

post:
	$(BLOGPOST) $(BLOGPOST_OPTS) $(ASCIIDOC_OPTS2) post $(SRCFILE)
	@echo "Make sure to update the category on Wordpress since it's erased"
