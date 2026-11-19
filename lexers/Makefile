# Builds the standalone quantum lexer.
# Requires: flex, bison/yacc, gcc (and libfl, e.g. `apt install flex bison libfl-dev`)

quantum_lexer: quantum_lexer.l support/plus-times-power.y support/quant.h
	yacc -d support/plus-times-power.y
	flex -o quantum_lexer.c quantum_lexer.l
	gcc -I support -c y.tab.c -Dmain=parser_main -o y.tab.o
	gcc -I support quantum_lexer.c y.tab.o -o quantum_lexer -lfl -lm

clean:
	rm -f quantum_lexer quantum_lexer.c y.tab.c y.tab.h y.tab.o
