# Manipulação de Listas em Prolog
## Introdução
A manipulação de listas é um dos conceitos fundamentais em Prolog, sendo amplamente utilizada para representar conjuntos de dados e realizar operações como inserção, remoção e busca de elementos. Listas permitem trabalhar com estruturas dinâmicas de forma simples e eficiente dentro da programação lógica.

## Parte Teórica
### Como funcionam as listas:
Listas em Prolog são estruturas que armazenam elementos de forma ordenada. Elas são definidas entre colchetes e podem conter qualquer tipo de dado.
```prolog
[4, X, casa(1, azul), a]
```
Uma lista também pode ser dividida em cabeça (Head) e cauda (Tail):
```prolog
[H | [b,c,d]]
[a | T]
```
Onde H é o primeiro elemento e T é o restante da lista

### Exemplos de predicados básicos:

list_to_set transforma uma lista em um **set**, onde set é um tipo de lista que não possui elementos repetidos:
```prolog
list_to_set(List, Set).
```
append é usado para concatenar listas:
```prolog
append(Lista1, Lista2, Lista3).  % concatena as listas 1 e 2 e forma a lista 3
append(ListaDeListas, Lista).    % retorna true se a Lista for uma concatenação das listas na ListaDeListas
```

sum_list soma todos os números de uma lista:
```prolog
sum_list(Lista, Soma).
```

## Parte Prática
### Exemplo 1:
Código utilizado é [movies](movies.pl) disponibilizado na aula do dia 15/04.

O objetivo é criar um predicado para contar a quantidade de usuários que recomendaram filmes:
```prolog
allusers(L) :- findall(U, likes(U, _),L).

countusers(C) :- allusers(U), length(U, C).
```
![](countusers.gif)

Este predicado segue o mesmo padrão do countgenres
```prolog
allgenres(R) :- findall(G,genre(_,G),L), list_to_set(L,R).
       
countgenres(C) :- allgenres(G), length(G, C).
```
Com a diferença do predicado list_to_set não ser necessário, já que cada usuário aparece apenas uma vez no código

### Exemplo 2:

Puzzle de lógica, o objetivo é descobrir a ordem, as cores, quem mora em cada casa e de quem é cada pet pelas informações dadas:
- Existem 3 casas alinhadas, cada uma com uma cor diferente: vermelha, verde e azul.
- Em cada casa vive uma pessoa: Alice, Bob e Carla.
- Cada pessoa tem um pet: gato, cachorro, hamster.
- Bob vive na casa vermelha.
- A pessoa que tem um gato vive na casa do meio.
- Carla tem um hamster e vive na casa ao lado da casa azul.
- A primeira casa é verde.
- Qual a cor, o morador e o pet de cada casa?

**Solução**
```prolog
ao_lado(X, Y, List) :- nextto(X, Y, List). % X à esquerda de Y
ao_lado(X, Y, List) :- nextto(Y, X, List). % Y à esquerda de X

solucao(Casas) :-
  Casas = [casa(_,verde,_),casa(_,_,gato),_],    %"A primeira casa é verde" e "A pessoa que tem um gato vive na casa do meio"
  member(casa(_,_,cachorro),Casas),              % Como não existem afirmações que envolvem o cachorro, a cor azul, e a Alice,
  member(casa(_,azul,_),Casas),                  % esses 3 fatos foram criados para indicar a existência deles.
  member(casa(alice,_,_),Casas),
  member(casa(bob,vermelha,_),Casas),            %"Bob vive na casa vermelha"
  member(casa(carla,_,hamster),Casas),           %"Carla tem um hamster"
  ao_lado(casa(carla,_,_),casa(_,azul,_),Casas). %"Carla vive ao lado da casa azul"
```

## Fontes:

- https://www.swi-prolog.org/pldoc/
- https://swish.swi-prolog.org
- http://www.learnprolognow.org/
- Material da professora
