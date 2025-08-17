
SHELL := bash

.PHONY: help
help:
	@echo 'make build         default target, builds the site into ./_site'
	@echo 'make serve         serve site locally out of ./_site'

.PHONY: build
build: static/favicon.ico static/ysap.png static/favicon.jpg
	mkdir -p _site _site/contact _site/static _site/episodes _site/resources
	# disable indexing for certain dirs
	echo -n > _site/static/index.html
	# copy static files
	cat static/robots.txt > _site/robots.txt
	#cat static/ysap.png > _site/static/ysap.png
	cat static/style.css > _site/static/style.css
	cat static/ansi.css > _site/static/ansi.css
	cat static/terminal.js > _site/static/terminal.js
	cat static/index.html > _site/index.html
	cat static/contact.html > _site/contact/index.html
	cat static/blogs.html > _site/blogs/index.html
	cat static/projects.html > _site/projects/index.html
	# make /ping endpoint (nginx handles this for me, but just in case)
	# create ASCII index page for curl users
	./make-index > _site/index.txt
	# create ASCII help page
	./make-help > _site/help
	# create episodes ASCII table
	./make-episodes > _site/episodes/index.txt
	# make episodes JSON file for curl
	./make-episodes-json > _site/json
	# make jsonp for our HTML files
	./make-commands-jsonp > _site/static/commands.js
	./make-episodes-json EPISODES > _site/static/episodes.js
	cat _site/json > _site/episodes.json

.PHONY: serve
serve:
	python3 -mhttp.server -d _site


