include ../common.mk

.PHONY: test
test: Colfer.go gen_test.go breaktest
	$(GO) test -v

Colfer.go: ../testdata/test.colf ../testdata/test-go.tags ../*.go ../cmd/colf/*.go
	$(COLF) -t ../testdata/test-go.tags Go ../testdata/test.colf
	mv gen/Colfer.go .
	rmdir gen

breaktest: ../testdata/break*.colf ../*.go ../cmd/colf/*.go
	$(COLF) -p github.com/pascaldekloe/colfer/go/$@ go ../testdata/break*.colf
	$(GO) build ./$@/...
	touch $@

.PHONY: clean
clean:
	rm -fr breaktest

.PHONY: clean-all
clean-all: clean
	rm -f Colfer.go
