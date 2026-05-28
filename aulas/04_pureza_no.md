# Métricas estatísticas para definir a pureza de um nó
É possível separar uma mistura, por exemplo, de itens, olhando e analisando as diferenças, porém a máquina precisa de uma medida. Diante disso, a árvore de decisão consegue saber se está separando bem os elementos analisando um índice.  

## Índice de Gini
A árvore de decisão contém uma métrica chamada de **Gini**. 

#### O que é? 
Pensando em um país, o índice de Gini mede o grau de desigualdade na distribuição de renda. De forma análoga, em uma árvore de decisão de **classificação**, o índice Gini mede o quanto as classes estão misturadas dentro de um nó.

Quando $Gini = 0$, o nó é puro, ou seja, todos os exemplos pertencem à mesma classe. Quanto maior o valor do Gini, mais misturadas estão as classes naquele nó. 
Em uma classificação com duas classes, o maior valor possível é **0,5**, quando o nó possui metade dos exemplos de cada classe.

Por exemplo, para classificar frutas entre maçã e banana:
- Nó com 10 maçãs e 0 bananas: $Gini = 0$, então o nó é puro.
- Nó com 5 maçãs e 5 bananas: $Gini = 0,5$, então temos a maior impureza possível para duas classes.

A árvore procura cortes que gerem nós mais puros, ou seja, com menor índice Gini.
Para isso, é feito o seguinte cálculo: 

$$
G = \frac{\displaystyle \sum_{i=1}^{n} \sum_{j=1}^{n} \left\| x_i - x_j \right\|}{2n^2 \bar{x}}
$$


## Entropia

A **entropia** também é uma medida de impureza utilizada em árvores de decisão de classificação. Ela indica o quanto as classes estão misturadas dentro de um nó.

Assim como no índice Gini:

- Se o nó contém apenas uma classe, a entropia é 0, pois o nó é puro.
- Se as classes estão bem misturadas, a entropia é maior.
- Em um problema com duas classes, a entropia máxima é 1, quando há metade dos exemplos de cada classe.

A fórmula da entropia é:

$$
H = - \sum_{i=1}^{k} p_i \log_2(p_i)
$$

Em que:

- $H$ é a entropia do nó;
- $k$ é a quantidade de classes;
- $p_i$ é a proporção de exemplos pertencentes à classe $i$.

Por exemplo, classificando frutas entre **maçã** e **banana**:

**Exemplo:** Nó com 10 maçãs e 0 bananas

$$
H = 0
$$

O nó é puro, pois todas as frutas pertencem à mesma classe.

**Exemplo:** Nó com 5 maçãs e 5 bananas

$$
H = - \left(0{,}5 \log_2(0{,}5) + 0{,}5 \log_2(0{,}5)\right) = 1
$$

Nesse caso, há máxima incerteza, pois o nó está igualmente dividido entre as duas classes.