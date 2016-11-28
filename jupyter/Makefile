NS = curiouslearner
REPO = jupyter_notebooks
VERSION = 0.1
DIR = jupyter_notebooks
NAME = notebooks
PORT = 8888

.PHONY: build up down log tag_latest

build:
	docker build -t $(NS)/$(REPO):$(VERSION) .

up:
	docker run \
		--name $(NAME) \
		-p $(PORT)\:$(PORT) \
		-v $(PWD)/$(DIR)\:/$(DIR):rw \
		$(NS)/$(REPO)\:$(VERSION) >> $(DIR)/log.file

down:
	docker rm -f $(NAME)

log:
	docker logs $(NAME) | awk '\
		{matched=0}\
		/INFO:/    {matched=1; print "\033[0;37m" $$0 "\033[0m"}\
		/WARNING:/ {matched=1; print "\033[0;34m" $$0 "\033[0m"}\
		/ERROR:/   {matched=1; print "\033[0;31m" $$0 "\033[0m"}\
		/Next/     {matched=1; print "\033[0;31m" $$0 "\033[0m"}\
		/ALERT:/   {matched=1; print "\033[0;35m" $$0 "\033[0m"}\
		/Stack trace:/ {matched=1; print "\033[0;35m" $$0 "\033[0m"}\
		matched==0            {print "\033[0;33m" $$0 "\033[0m"}\
	'

tag_latest:
	docker tag $(NS)/$(REPO)\:$(VERSION) $(NS)/$(REPO)\:latest
