#####################

NCC = "D:\Langs\Nemerle\net-4.0\ncc.exe"
DEBUG =
TESTS =

SOURCES_BASE = console.n reader.n types.n
SOURCES_LISP = env.n
SOURCES = $(SOURCES_BASE) $(SOURCES_LISP)

#####################

SRCS = step0_repl.n step1_read_print.n

LIB_SRCS = $(filter-out step%, $(SOURCES))

FLAGS = $(if $(strip $(DEBUG)),-debug+,)

#####################

all: $(patsubst %.n,%.exe,$(SRCS))

%.exe: %.n mal.dll
	$(NCC) $(FLAGS) -r:mal.dll -out:$@ $<

mal.dll: $(LIB_SRCS) getline.dll
	$(NCC) $(FLAGS) -target:library -r:getline.dll $(filter-out getline.dll, $+) -out:$@

getline.dll: getline.cs
	$(NCC) $(FLAGS) -target:library -nowarn:10001 -nowarn:10003 \
		-nowarn:10005 -nowarn:10011 -nowarn:10013 -nowarn:168 $+ -out:$@

clean:
	rm -f *.dll *.exe *.mdb *.pdb
