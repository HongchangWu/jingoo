PPRINT:=camlp4 pr_o.cmo pa_o.cmo
PKG:=pcre,unix,uutf,dynlink
CMPL:=ocamlfind ocamlopt -g -package $(PKG) -linkpkg -I ../src ../src/jingoo.cmxa
JG_CMPL:=../src/compiler
TARGET:= my_ext.cmxs simple advanced bench

#.PHONY:$(TARGET)
all: $(TARGET)

my_ext.cmxs: my_ext.ml
	$(CMPL) -shared -o $@ $<

simple: test_data.ml simple.ml
	$(CMPL) -o $@ test_data.ml simple.ml

advanced: test_data.ml advanced.ml
	$(CMPL) -o $@ test_data.ml advanced.ml

# benchmark for interp mode: ./bench
# benchmark for compiler mode: ./bench -cmpl
bench: bench.ml
	$(CMPL) -o $@ test_data.ml bench.ml

clean:
	rm -f *.cmi *.cmo *.cmx *.o *.cmxs
	rm -f $(TARGET)

rebuild: clean all

.PHONY: rebuild clean all
