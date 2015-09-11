#####################

NCC = "D:\Langs\Nemerle\net-4.0\ncc.exe"
DEBUG =
TESTS =

SOURCES_BASE = types.n
SOURCES_LISP = env.n
SOURCES = $(SOURCES_BASE) $(SOURCES_LISP)

OTHER_SOURCES = getline.n

#####################

SRCS = step0_repl.n

LIB_SRCS = $(filter-out step%,$(OTHER_SOURCES) $(SOURCES))

FLAGS = $(if $(strip $(DEBUG)),-debug+,)

#####################

all: step0_repl.exe

%.exe: %.n mal.dll
	$(NCC) $(FLAGS) -r:mal.dll -out:$@ $<

mal.dll: $(LIB_SRCS)
	$(NCC) $(FLAGS) -target:library $+ -out:$@

clean:
	rm -f *.dll *.exe *.mdb *.pdb
