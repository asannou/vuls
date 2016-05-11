.PHONY: \
	all \
	vuls \
	go-cve-dictionary \
	go-cve-dictionary-2015

all: vuls

vuls: go-cve-dictionary
	docker build -t asannou/vuls -f Dockerfile .

go-cve-dictionary: go-cve-dictionary-2015
	docker build --no-cache -t asannou/go-cve-dictionary -f Dockerfile.go-cve-dictionary .

go-cve-dictionary-2015:
	docker build -t asannou/go-cve-dictionary:2015 -f Dockerfile.go-cve-dictionary-2015 .
