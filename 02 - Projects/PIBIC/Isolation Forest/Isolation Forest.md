---
tags:
  - unicap
  - pibic
---

##### Artigo: 
![[Liu et al. - 2008 - Isolation Forest.pdf]]
##### Apresentação do Paper:
![[Presentation - Isolation Forest.pdf]]
##### Roteiro da Apresentação:
![[Isolation Forest - Roteiro.pdf]]

##### Formalização do Algoritmo
- [Overleaf - Algoritmos](https://www.overleaf.com/7132172517jspcnmsvprbb#f2cbe4)

1. Mudança de paradigma
	- A maioria das abordagens tradicionais para detecção de anomalias opera sob um paradigma comum: construir um modelo quantitativo do que constitui um comportamento "normal" e, em seguida, identificar instâncias que se desviam significativamente desse perfil.
	- O algoritmo Isolation Forest (iForest) representa uma inversão fundamental dessa abordagem. Em vez de modelar a normalidade, ele procura ativamente "isolar explicitamente as anomalias".
	- Essa mudança de perspectiva é a fonte primária da notável eficiência do algoritmo.
	-  o ato de "separar uma instância do resto dos dados" é uma operação conceitualmente mais simples e computacionalmente menos dispendiosa. A eficiência do iForest não é meramente um detalhe de implementação, mas uma consequência direta de sua filosofia central. Ao focar na propriedade de "isolabilidade", o algoritmo evita a necessidade de cálculos de distância ou densidade entre pares de pontos, que escalam de forma pobre com o tamanho e a dimensionalidade do conjunto de dados. A operação fundamental do iForest — uma partição binária aleatória — é computacionalmente barata e agnóstica à distribuição dos dados. O objetivo não é construir um modelo perfeito, mas sim encontrar o caminho mais curto para o isolamento. Como as anomalias são, por natureza, mais fáceis de separar, o algoritmo pode concluir sua tarefa para um ponto anômalo muito mais rapidamente do que um método tradicional poderia construir um perfil de densidade local completo, o que fundamenta sua complexidade de tempo linear.
2. Poucos e Diferentes
	- O sucesso do princípio de isolamento repousa sobre uma hipótese fundamental a respeito da natureza das anomalias, que podem ser caracterizadas por duas propriedades quantitativas: i) elas são a minoria, consistindo em menos instâncias, e ii) elas possuem valores de atributos que são muito diferentes daqueles das instâncias normais.
	- A propriedade "poucos" implica que, em um processo de particionamento recursivo, menos divisões são necessárias para separar um pequeno grupo de anomalias do grupo muito maior de pontos normais. A propriedade "diferentes" sugere que uma divisão aleatória em um atributo qualquer tem uma alta probabilidade de separar com sucesso um ponto anômalo do restante dos dados, pois seu valor de atributo provavelmente se encontrará em uma região esparsamente populada do espaço de características.
3. Algoritmos
	- Seja $X \in \mathbb{R}^{n * d}$ a matriz de dados de entrada, com $n$ instâncias e $d$ atributos. Cada instância é um vetor $x_i \in \mathbb{R}^d$. O conjunto de índices de atributos é denotado por $Q = \{1, 2,..., d\}$. Uma iTree é uma árvore binária composta por dois tipos de nós:
		- `InternalNode(q, p, left, right)`: Um nó interno que contém um índice de atributo de divisão $q \in Q$, um valor de divisão $p \in \mathbb{R}$, e referências aos seus filhos esquerdo (`left`) e direito (`right`).
		- `ExternalNode(size)`: Um nó terminal (folha) que contém o número de instâncias, `size`, que terminaram neste nó.
	- Algoritmo 1: `Build-iTree(X', e, l)`
		- A construção de uma única iTree é um processo recursivo que particiona um subconjunto de dados.
		- **Entrada:**
		    - $X' \subseteq X$: Um subconjunto dos dados de entrada.
		    - $e \in \mathbb{N}_0$: A altura atual da árvore (profundidade do nó), com $e=0$ na raiz.
		    - $l \in \mathbb{N}$: O limite de altura da árvore.
		- **Saída:** O nó raiz de uma iTree.
		- **Procedimento:**
		    1. **Condição de Parada:** Se $e \ge l$ ou $|X'| \le 1$, então **retorne** `ExternalNode(|X'|)`.
		    2. **Seleção de Atributo:** Seja $q$ um elemento selecionado uniformemente ao acaso do conjunto de atributos $Q$.
		    3. **Seleção do Ponto de Divisão:** Sejam $min_q = \min(\{x_q | x \in X'\})$ e $max_q = \max(\{x_q | x \in X'\})$. Seja $p$ um número real selecionado uniformemente ao acaso do intervalo $[min_q, max_q]$.
		    4. **Particionamento dos Dados:**
		        - Seja $X_l = \{x \in X' | x_q < p\}$.
		        - Seja $X_r = \{x \in X' | x_q \ge p\}$.
		    5. **Chamada Recursiva:** **Retorne** `InternalNode(q, p, Build-iTree(X_l, e+1, l), Build-iTree(X_r, e+1, l))`.
	-  Algoritmo 2: `Build-iForest(X, t, ψ)`
		- A floresta é construída como um ensemble de iTrees, cada uma treinada em uma subamostra dos dados.
		- **Entrada:**
		    - $X$: O conjunto de dados de entrada completo.
		    - $t \in \mathbb{N}$: O número de árvores a serem construídas no ensemble.
		    - $\psi \in \mathbb{N}$: O tamanho da subamostragem.
		- **Saída:** Uma floresta $F = \{T_1, T_2,..., T_t\}$, um conjunto de iTrees.
		- **Procedimento:**
		    1. Inicialize um conjunto vazio $F$.
		    2. Defina o limite de altura $l = \lceil\log_2(\psi)\rceil$.
		    3. Para $i$ de 1 até $t$:
		        1. Seja $X'_i$ um subconjunto de $X$ de tamanho $\psi$, amostrado sem reposição.
		        2. Seja $T_i = \text{Build-iTree}(X'_i, 0, l)$.
		        3. Adicione $T_i$ ao conjunto $F$.
	    1. **Retorne** $F$.
	- Algoritmo 3: `Compute-PathLength(x, T)`
		- O comprimento do caminho de uma instância $x$ é o número de arestas percorridas da raiz de uma iTree $T$ até um nó terminal.
		- **Entrada:**
		    - $x \in \mathbb{R}^d$: Uma instância de dados.
		    - $T_{node}$: O nó atual da iTree sendo avaliado, começando com a raiz $T$.
		- **Saída:** O comprimento do caminho de $x$.
		- **Procedimento (definido recursivamente como $h(x, T_{node})$):**
		    1. **Caso Base:** Se $T_{node}$ é um `ExternalNode(size)`:
		        - **Retorne** $c(\text{size})$, onde $c$ é uma função de ajuste para nós terminais com mais de um membro. O comprimento do caminho efetivo até este ponto é a profundidade $e$. A definição formal é $h(x, T) = e + c(T.\text{size})$.1 A justificativa para $c(\text{size})$ será detalhada na próxima seção.
		    2. **Passo Recursivo:** Se $T_{node}$ é um `InternalNode(q, p, left, right)`:
		        - Seja $x_q$ o valor do atributo $q$ na instância $x$.
		        - Se $x_q < p$, então **retorne** $1 + h(x, \text{left})$.
		        - Senão, **retorne** $1 + h(x, \text{right})$.
4. teoria
	- A pontuação de anomalia é o cerne do mecanismo de detecção do iForest. Sua formulação não é arbitrária, mas sim fundamentada em resultados clássicos da ciência da computação sobre a estrutura de árvores binárias aleatórias.
	- O comprimento bruto do caminho, $h(x)$, de uma instância não é, por si só, uma medida de anomalia universalmente comparável. Um caminho de comprimento 10 em uma árvore construída a partir de uma amostra de 1000 pontos tem um significado diferente de um caminho de mesmo comprimento em uma árvore construída a partir de 32 pontos. Para tornar os comprimentos de caminho significativos e comparáveis entre diferentes árvores e tamanhos de amostra, é necessária uma normalização.
	- O algoritmo introduz um fator de normalização, $c(n)$, que representa o comprimento de caminho médio esperado para um ponto qualquer em uma árvore construída aleatoriamente com $n$ instâncias. A pontuação de anomalia, $s(x, n) = 2^{-\frac{E(h(x))}{c(n)}}$, utiliza a razão entre o comprimento de caminho médio observado para um ponto $x$, $E(h(x))$, e este comprimento de caminho esperado, $c(n)$. Esta razão quantifica o quão mais curto (anômalo) ou mais longo (normal) é o caminho de um ponto em relação à expectativa.
	- A justificativa para a fórmula específica de $c(n)$ reside em uma poderosa analogia estrutural. Uma iTree, construída através de partições recursivas e aleatórias, é estruturalmente análoga a uma Árvore de Busca Binária (BST, do inglês _Binary Search Tree_) construída a partir da inserção de chaves em ordem aleatória. O insight crucial é que o processo de isolar um ponto em uma iTree é conceitualmente equivalente a uma _busca malsucedida_ em uma BST. Uma busca por um elemento que não está presente em uma BST percorre um caminho da raiz até encontrar um ponteiro nulo (um nó externo), que representa o local onde o elemento seria inserido. Da mesma forma, em uma iTree, um ponto é isolado quando a partição o coloca sozinho em um nó terminal (externo). Portanto, $c(n)$ é definido precisamente como o comprimento médio do caminho de uma busca malsucedida em uma BST aleatória com $n$ nós.
	- Caminho Interno ($I_n$) como a soma das profundidades de todos os nós internos.
	- Comprimento do Caminho Externo ($E_n$) como a soma das profundidades de todos os nós externos (folhas ou ponteiros nulos).
	- Um teorema fundamental relaciona essas duas quantidades: $$E_n = I_n + 2n$$.
	- Uma árvore com $n$ nós internos possui $n+1$ nós externos. O comprimento médio de uma busca malsucedida, $U_n$, é, portanto, a média do comprimento do caminho externo: $$U_n = \frac{E_n}{n+1}$$.
	- Para uma BST construída a partir de inserções aleatórias, pode-se mostrar através de relações de recorrência que o comprimento médio do caminho externo é aproximadamente $2 \ln n$. A fórmula exata usada no artigo do iForest para $c(n)$ é: $$c(n) = 2H_{n-1} - \frac{2(n-1)}{n}$$onde $H_k$ é o $k$-ésimo **Número Harmônico**, definido como $H_k = \sum_{i=1}^{k} \frac{1}{i}$.1 Esta fórmula é uma forma específica do resultado geral para o comprimento médio de busca malsucedida em BSTs.
	- Para valores grandes de $k$, o número harmônico pode ser aproximado por $$H_k \approx \ln(k) + \gamma$$onde $\gamma \approx 0.5772156649$ é a constante de Euler-Mascheroni. Esta aproximação explica o uso de constantes numéricas específicas em implementações do algoritmo para estimar $c(n)$.
	- A fórmula da pontuação, $s(x,n)=2^{-\frac{E(h(x))}{c(n)}}$, mapeia a razão normalizada do comprimento do caminho para um intervalo entre 0 e 1 de forma exponencial.1 O comportamento desta função pode ser analisado em três cenários principais:
		- **Caso 1: Anomalia Clara:** Se uma instância $x$ é facilmente isolada, seu comprimento de caminho médio, $E(h(x))$, se aproxima de 0. A razão $\frac{E(h(x))}{c(n)}$ também se aproxima de 0. Consequentemente, a pontuação $s(x,n) = 2^{-0} = 1$. Uma pontuação próxima de 1 é um forte indicador de anomalia.
		- **Caso 2: Ponto Normal (Médio):** Se o comprimento de caminho médio de uma instância é próximo da média esperada para o tamanho da amostra, então $E(h(x)) \approx c(n)$. A razão é aproximadamente 1, e a pontuação é $s(x,n) \approx 2^{-1} = 0.5$. Uma pontuação próxima de 0.5 sugere que a instância é normal.
		- **Caso 3: Ponto Normal (Profundo):** Se uma instância está profundamente aninhada em um cluster denso de pontos normais, será muito difícil de isolar, e seu comprimento de caminho médio se aproximará do máximo possível, $n-1$. A razão $\frac{E(h(x))}{c(n)}$ será significativamente maior que 1, resultando em um expoente negativo de grande magnitude e uma pontuação $s(x,n)$ que se aproxima de 0.
5. Hiperparametros
	- Uma única iTree é inerentemente instável; devido à natureza aleatória da seleção de atributos e pontos de divisão, o comprimento do caminho para uma mesma instância pode variar drasticamente entre diferentes execuções. Para mitigar essa variância, o iForest emprega um ensemble de árvores, e a pontuação final é baseada no comprimento médio do caminho sobre todas as árvores da floresta.
		- Os autores do algoritmo descobriram empiricamente que o desempenho da detecção converge rapidamente com um número relativamente pequeno de árvores. Os gráficos de convergência mostram que os comprimentos médios de caminho, tanto para anomalias quanto para pontos normais, tendem a se estabilizar em torno de $t=100$ árvores.1 Adicionar mais árvores além deste ponto geralmente resulta em melhorias marginais na estabilidade da pontuação, ao custo de um aumento linear no tempo de computação.4 Portanto, $t=100$ é considerado um ponto de retornos decrescentes, oferecendo um bom compromisso entre robustez e eficiência. A eficácia do mecanismo central do iForest é tal que um ensemble modesto é suficiente para produzir um ranking de anomalias estável e preciso.
	- O uso de subamostragem é uma inovação chave do iForest, com múltiplos benefícios estratégicos. O valor padrão frequentemente utilizado é $\psi=256$. 
		- Primeiramente, a subamostragem é uma técnica eficaz para combater os problemas de "swamping" e "masking". "Swamping" ocorre quando um grande número de pontos normais torna difícil a distinção de anomalias. "Masking" ocorre quando um grupo de anomalias próximas umas das outras mascara a presença individual de cada uma, fazendo com que pareçam um pequeno cluster normal.1 Ao treinar cada árvore em uma pequena subamostra aleatória dos dados, a densidade de pontos normais é reduzida, e a probabilidade de múltiplas anomalias acabarem na mesma amostra e se mascararem mutuamente também diminui. Isso efetivamente amplifica o sinal anômalo, tornando as anomalias mais fáceis de isolar.
		- Em segundo lugar, o tamanho da subamostragem controla implicitamente a complexidade das árvores. Com $\psi=256$, o limite de altura padrão da árvore é definido como $l = \lceil \log_2(256) \rceil = 8$.6 Esta profundidade é pequena o suficiente para prevenir que as árvores se ajustem excessivamente aos dados da subamostra (overfitting) e para garantir que a construção e a avaliação da árvore sejam extremamente rápidas.
6. Complexidade e Paralelização
	- O iForest exibe uma complexidade de tempo linear com uma constante baixa e um requisito de memória reduzido, tornando-o adequado para grandes conjuntos de dados.
		- **Complexidade de Tempo (Treinamento):** O treinamento envolve a construção de $t$ árvores. Cada árvore é construída a partir de uma subamostra de tamanho $\psi$. O tempo para construir uma árvore binária balanceada de tamanho $\psi$ é da ordem de $O(\psi \log \psi)$. Portanto, o tempo total de treinamento é $O(t \cdot \psi \log \psi)$. Como $t$ e $\psi$ são hiperparâmetros que não crescem com o tamanho do conjunto de dados original $n$, a complexidade do treinamento é efetivamente independente de $n$, tornando o algoritmo extremamente escalável.
		- **Complexidade de Tempo (Inferência):** Para pontuar uma nova instância, ela deve ser percorrida em cada uma das $t$ árvores. O comprimento médio do caminho em uma árvore de tamanho $\psi$ é da ordem de $O(\log \psi)$. Assim, o tempo total de inferência por instância é $O(t \log \psi)$.
		- **Complexidade de Espaço:** O modelo requer o armazenamento das $t$ árvores. Cada árvore, construída a partir de $\psi$ amostras, tem um tamanho de $O(\psi)$. A complexidade de espaço total é, portanto, $O(t \cdot \psi)$, que é constante e independente do tamanho do conjunto de dados de treinamento original.
	- A arquitetura do iForest é inerentemente paralelizável. A construção de cada uma das $t$ iTrees é um processo completamente independente; a árvore $T_i$ não depende de nenhuma outra árvore $T_j$ (para $i \neq j$). Essa propriedade torna o algoritmo "embaraçosamente paralelo", ideal para exploração em sistemas multi-core.
		- Com $P$ processadores, o tempo de treinamento teórico pode ser reduzido por um fator de até $P$, aproximando-se de $O(\frac{t}{P} \cdot \psi \log \psi)$. Esta escalabilidade permite a construção rápida de florestas muito grandes ou a análise de conjuntos de dados massivos em tempo hábil.