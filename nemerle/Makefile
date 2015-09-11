#####################

NCC = "D:\Langs\Nemerle\net-4.0\ncc.exe"
DEBUG =
TESTS =

SOURCES_BASE = types.n
SOURCES_LISP = env.n
SOURCES = $(SOURCES_BASE) $(SOURCES_LISP)

OTHER_SOURCES = console.n

#####################

SRCS = step0_repl.n

LIB_SRCS = $(filter-out step%,$(OTHER_SOURCES) $(SOURCES))

FLAGS = $(if $(strip $(DEBUG)),-debug+,)

#####################

all: step0_repl.exe

%.exe: %.n mal.dll
	$(NCC) $(FLAGS) -r:mal.dll -out:$@ $<

mal.dll: $(LIB_SRCS) getline.dll
	$(NCC) $(FLAGS) -target:library -r:getline.dll $(filter-out getline.dll, $+) -out:$@

getline.dll: getline.cs
	$(NCC) $(FLAGS) -target:library -nowarn:10001 -nowarn:10003 \
		-nowarn:10005 -nowarn:10011 -nowarn:10013 -nowarn:168 $+ -out:$@

clean:
	rm -f *.dll *.exe *.mdb *.pdb
