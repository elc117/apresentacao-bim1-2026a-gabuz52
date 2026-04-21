# Manipulação de Listas em Prolog
## Introdução
A manipulação de listas é um dos conceitos fundamentais em Prolog, sendo amplamente utilizada para representar conjuntos de dados e realizar operações como inserção, remoção e busca de elementos. Listas permitem trabalhar com estruturas dinâmicas de forma simples e eficiente dentro da programação lógica.

## Parte Teórica
### - Como funcionam as listas:
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

### - Exemplos de predicados básicos:

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



## Fontes:

- https://www.swi-prolog.org/pldoc/
- https://swish.swi-prolog.org
- http://www.learnprolognow.org/
- Material da professora
