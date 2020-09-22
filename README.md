# APS-Logica EBNF Linguagem
OBS: README sem os <>, leia o txt

ENBF Linguagem "PorExtenso++"

DIGITO ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

CARACTER ::= "a" | "b" | ... | "z" | "A" | "B" | ... | "Z" | "@" | ... | "." | "#"

INTEIRO ::= DIGITO+

FLOAT ::= DIGITO+ "." DIGITO+

NUMERO ::= INTEIRO | FLOAT

STRING  ::= CARACTER+

BOOLEANO ::= "TRUE" | "FALSE"

OPS_SOMA ::= "mais" | "menos"

OPS_MULT ::=  "vezes" | "dividido"

OPS_COMPARAR ::= "igual" | "diferente" | "menor" | "menorigual" | "maior" | "maiorigual"

VARIAVEL ::= CARACTER (DIGITO | CARACTER)*

COMPARACAO ::= ((VARIAVEL | NUMERO | BOOLEANO) OPS_COMPARAR (VARIAVEL | NUMERO | BOOLEANO)) | BOOLEANO

EXPRESSAO ::= ( TERMO (OPS_SOMA EXPRESSAO)+ ) | (TERMO | COMPARACAO)

TERMO ::= (EXPRESSAO_PARENTESES (OPS_MULT TERMO)+ ) | EXPRESSAO_PARENTESES 

EXPRESSAO_PARENTESES ::= "(" EXPRESSAO ")" | (NUMERO | STRING | VARIAVEL)

COND ::= IF | WHILE

IF ::= "se-e-somente-se" COMPARACAO "{" (EXPRESSAO | COND) "}" | "se-e-somente-se" COMPARACAO "{" (EXPRESSAO | COND) "}" "casocontrario" "{" (EXPRESSAO | COND) "}"

WHILE ::= "enquanto" COMPARACAO "{" (EXPRESSAO | COND) "}"

PROGRAMA ::= (EXPRESSAO | COND)*
