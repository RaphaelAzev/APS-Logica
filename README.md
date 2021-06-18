# APS-Logica EBNF Linguagem
FUNCTION = TYPE, IDENTIFIER, "(", [{PARAM}], ")", BLOCK ;

PARAM = TYPE, IDENTIFIER ;

RETURN = "retornar", (EXPRESSION | OREXPR), ";" ;

BLOCK = "{", { COMMAND }, "}";

COMMAND = ( λ | VARIABLE_DECLARATION | ASSIGNMENT | PRINT | IF | WHILE | BLOCK | FUNCTION_CALL), ";" ;

FUNCTION_CALL = TYPE, IDENTIFIER, "(", (EXPRESSION | OREXPR), {",", (EXPRESSION | OREXPR)}, ")", ";"
VARIABLE_DECLARATION = ( TYPE, " ", IDENTIFIER, "recebe, EXPRESSION ) |
                       ( TYPE, " ", IDENTIFIER );

ASSIGNMENT = IDENTIFIER, "recebe, EXPRESSION ;

PRINT = "imprimir", "(", EXPRESSION, ")" ;

READ = "ler", "(", INT, ")" ;

WHILE = "enquanto", "(", OREXPR, ")", COMMAND;

IF = "se_e_somente_se", "(", OREXPR, ")", COMMAND |
     "se_e_somente_se", "(", OREXPR, ")", COMMAND, "casocontrario", COMMAND;

OREXPR = ANDEXPR, {"ou", ANDEXPR};
ANDEXPR = EQEXPR, {"e", EQEXPR};
EQEXPR = RELEXPR, {"igual", RELEXPR};
RELEXPR = EXPRESSION, {("maior" | "menor"), EXPRESSION};
EXPRESSION = TERM, { ("mais" | "menos"), TERM } ;
TERM = FACTOR, { ("vezes" | "dividido"), FACTOR } ;
FACTOR = (("mais" | "menos" | "negar"), FACTOR) | NUMBER | BOOL_VALUE | STRING_VALUE | "(", EXPRESSION, ")" | IDENTIFIER ;

TYPE = INT | BOOL | STRING;
INT = "inteiro";
BOOL = "booleano";
STRING = "string";

IDENTIFIER = LETTER, { LETTER | "_"} ;
NUMBER = DIGIT, { DIGIT } ;
BOOL_VALUE = "verdadeiro" | "falso" ;
STRING_VALUE = '"', ( LETTER | NUMBER ), {( LETTER | NUMBER )}, '"';
LETTER = a | ... | z | A | ... | Z;
DIGIT = 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 0 ;

# Linguagem porextenso
<p>Para o projeto, foi se desenvolvido uma linguagem que tem seus operadores e operações escritas por extenso.  
Com uma estrutura baseada em C++, ela </p>  
<p>A linguagem por extenso tem como objetivo facilitar o entendimento de códigos para pessoas que não são versadas nas nuâncias de programação, visando deixar mais aparente  
o que está acontecendo nas linhas de código. Enquanto ela ainda é rigida em sua formatação de blocos de códigos (precisa ter main declarado, precisa de ; no final de linhas,  
precisa de abertura de blocos), ela produz códigos mais simples de explicar, como por exemplo trazendo operações como == para sua forma literal "igual"</p>  


O codigo em porextenso a seguir:  

```
inteiro main() {
    inteiro x;
    x recebe ler();
    se_e_somente_se(x maior 0) {
        imprimir(x);
    } casocontrario {
        enquanto(x menor 0) {
            x recebe x mais 1;
            imprimir(x);
        }
    }
}
```
Equivale ao codigo em C++ abaixo:  

```C++
int main() {
    int x;
    std::cin >> x;
    if(x > 0) {
        std::cout << x;
    } else {
        while(x < 0) {
            x = x + 1;
            std::cout << x;
        }
    }
}
```

> Para compilar programa em porextenso com o compilador porextenso.py, deve se rodar ele dessa forma:  
> - python3 porextenso.py arquivo.porextenso
> OBS: O compilador so aceita arquivos do format .porextenso.