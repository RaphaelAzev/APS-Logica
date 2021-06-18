# USO

> Para compilar programa em porextenso com o compilador porextenso.py, deve se rodar ele dessa forma:  
> - python3 porextenso.py arquivo.porextenso  
> OBS: O compilador so aceita arquivos do format .porextenso.

# APS-Logica EBNF Linguagem
> FUNCTION = TYPE, IDENTIFIER, "(", [{PARAM}], ")", BLOCK ;  
> 
> PARAM = TYPE, IDENTIFIER ;  
> 
> RETURN = "retornar", (EXPRESSION | OREXPR), ";" ;  
> 
> BLOCK = "{", { COMMAND }, "}";  
> 
> COMMAND = ( λ | VARIABLE_DECLARATION | ASSIGNMENT | PRINT | IF | WHILE | BLOCK | FUNCTION_CALL), ";" ;  
> 
> FUNCTION_CALL = TYPE, IDENTIFIER, "(", (EXPRESSION | OREXPR), {",", (EXPRESSION | OREXPR)}, ")", ";"  
> VARIABLE_DECLARATION = ( TYPE, " ", IDENTIFIER, "recebe, EXPRESSION ) | ( TYPE, " ", IDENTIFIER );  
>  
> ASSIGNMENT = IDENTIFIER, "recebe, EXPRESSION ;  
>  
> PRINT = "imprimir", "(", EXPRESSION, ")" ;  
>  
> READ = "ler", "(", INT, ")" ;  
>  
> WHILE = "enquanto", "(", OREXPR, ")", COMMAND;  
>  
> IF = "se_e_somente_se", "(", OREXPR, ")", COMMAND | "se_e_somente_se", "(", OREXPR, ")", COMMAND, "casocontrario", COMMAND;  
>   
> OREXPR = ANDEXPR, {"ou", ANDEXPR};  
> ANDEXPR = EQEXPR, {"e", EQEXPR};  
> EQEXPR = RELEXPR, {"igual", RELEXPR};  
> RELEXPR = EXPRESSION, {("maior" | "menor"), EXPRESSION};  
> EXPRESSION = TERM, { ("mais" | "menos"), TERM } ;  
> TERM = FACTOR, { ("vezes" | "dividido"), FACTOR } ;  
> FACTOR = (("mais" | "menos" | "negar"), FACTOR) | NUMBER | BOOL_VALUE | STRING_VALUE | "(", EXPRESSION, ")" | IDENTIFIER ;  
>   
> TYPE = INT | BOOL | STRING;  
> INT = "inteiro";  
> BOOL = "booleano";  
> STRING = "string";  
> 
> IDENTIFIER = LETTER, { LETTER | _ } ;  
> NUMBER = DIGIT, { DIGIT } ;  
> BOOL_VALUE = "verdadeiro" | "falso" ;  
> STRING_VALUE = '"', ( LETTER | NUMBER ), {( LETTER | NUMBER )}, '"';  
> LETTER = a | ... | z | A | ... | Z;  
> DIGIT = 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 0 ;  

# Linguagem porextenso
<p>Para o projeto, foi se desenvolvido uma linguagem que tem seus operadores e operações escritas por extenso. 
Com uma estrutura baseada em C++, ela facilita programadores familiares com linguagens semelhantes a aprenderem essa nova linguagens mantendo muitas das mesmas construções  
existentes em C++, como declarção de funções e um main que executa tudo, tipagem de variáveis e definição de blocos com chaves ( { } ).</p>  
<p>A linguagem por extenso tem como objetivo facilitar o entendimento de códigos para pessoas que não são versadas nas nuâncias de programação, visando deixar mais aparente  
o que está acontecendo nas linhas de código. Enquanto ela ainda é rigida em sua formatação de blocos de códigos (precisa ter main declarado, precisa de ; no final de linhas,  
precisa de abertura de blocos), ela produz códigos mais simples de explicar, como por exemplo trazendo operações como == para sua forma literal "igual"</p>  


O codigo em porextenso a seguir declara uma variável do tipo inteiro x e recebe um valor lido pelo input do usuário, após isso, se e somente se o valor de x for maior que 0  
irá se imprimir o valor de x no terminal, caso contrário enquanto x for menor que 0, somamos 1 ao seu valor e imprimimos. Veja o código abaixo:  

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
Perceba como explicar o código foi praticamente equivalente a ler ele como está escrito. Esse mesmo código equivale ao codigo em C++ abaixo:  

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

Muito menos intuitivo para uma pessoa entender com facilidade.  
  

## Dificuldades
<p>Por mais que porextenso oferece uma simplicidade no entendimento do código, ela dificulta a escrita do mesmo.  
Escrever tudo por extenso pode ser menos prático para pessoas ja versadas no uso de outras linguagens, além do fato
de que por extenso não oferece algo que outras linguagens não tenham, portanto não seria a melhor ferramenta para  
colocar serviços em produção.</p>  
  

## Mudanças
<p>Originalmente porextenso iria ter tudo por extenso, inclusive os números, mas devido a dificuldade mencionada acima  
foi-se optado por manter digitos como são originalmente, visto que o entendimento de numerais não necessariamente é  
algo somente para pessoas versadas em programação.</p>
<p>Para uma segunda iteração da linguagem, possíveis adições seriam traduzir também a abertura e fechadura de blocos  
de chaves, deixando ela de mais alto nível, próxima a linguagem humana. Além disso também implementar mais algumas  
operações, como resto de divisão (%), potência (**), etc.</p>  
  

  
## Operadores, métodos e tipos  
> C++ --> porextenso | Exemplo  
> - && --> e | x e y  
> - || --> ou | x ou y   
> - (+) --> mais | x mais y  
> - (-) --> menos | x menos y  
> - (*) --> vezes | x vezes y  
> - (/) --> dividido | x dividido y  
> - (>) --> maior | x maior y  
> - (<) --> menor | x menor y  
> - (=) --> recebe | x recebe y  
> - (==) --> igual | x igual y  
> - (!) --> negar | negar x  
> - std::cout --> imprimir() | imprimir(x)  
> - std::cin --> ler() | ler(x)  
> - if / else --> se_e_somente_se | se_e_somente_se(x igual verdadeiro) { } casocontrario {}  
> - while --> enquanto | enquanto(x maior 0)
> - int --> inteiro | inteiro x = 5;
> - bool / true / false --> booleano / verdadeiro / falso | booleano x recebe verdadeiro
> - string --> string | string x recebe "nao mudou muito essa parte"
> - return --> retornar | retornar x
