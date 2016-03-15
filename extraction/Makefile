CC= $(CAMLBIN)ocamlopt
FLAGS = -cclib -lunix
LIB= unix.cmxa

LEX= $(CAMLBIN)ocamllex
YACC= $(CAMLBIN)ocamlyacc

OBJ_I = dyade.cmx \
	parser.cmi

OBJ= 	dyade.cmx \
	lexer.cmx \
	parser.cmx \
	main.cmx \

PROG= dyade


all : 	$(PROG)

$(PROG) :  $(OBJ_I) $(OBJ)	
	$(CC) $(FLAGS) -o $(PROG) $(LIB) $(OBJ) 

dyade.mli :
	cp ../dyade.mli dyade.mli

dyade.ml : 
	cp ../dyade.ml dyade.ml

parser.ml parser.mli : parser.mly
	$(YACC) parser.mly

lexer.ml : lexer.mll
	$(LEX) lexer.mll

%.cmi : %.mli
	$(CC) -c $<

%.cmx : %.ml
	$(CC) -c $<	 


clean : 	
	rm -f *.o *.cmx *.cmi \
	$(PROG) \
	dyade.ml \
	lexer.ml \
	parser.ml \
	parser.mli

install :
	true

parser.mli : dyade.cmi
lexer.cmx : parser.cmi
main.cmx : dyade.cmx
parser.cmx : dyade.cmx
