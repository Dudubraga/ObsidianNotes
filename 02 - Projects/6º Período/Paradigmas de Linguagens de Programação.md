---
tags:
  - unicap
  - graduação
  - 6-periodo
---

**Professor:** Paulo Rocha
**Período:** Ago 2025 - Dez 2025
**Nota final:** TBA

# 1GQ
### Materiais de Apoio:
- [[Paradigmas - Aula 01 - Apresentação de Conceitos.pdf]]
- [[Paradigmas - Aula 02 - História.pdf]]
- [[Paradigmas - Aula 03 - Sintaxe e Semântica.pdf]]
- [[Paradigmas - Aula 04 - Nomes Vinculações e Escopos.pdf]]
- [[Paradigmas - Aula 05 - Tipos de Dados.pdf]]

### Conceitos Fundamentais:
##### Motivações e Critérios de Avaliação
O estudo dos conceitos de linguagens de programação transcende a mera aprendizagem de sintaxes específicas; ele equipa o desenvolvedor com um entendimento fundamental que permite a resolução de problemas de forma mais eficaz e elegante. A avaliação de uma linguagem de programação é um processo multifacetado que se baseia em um conjunto de critérios inter-relacionados. Os quatro critérios principais são legibilidade, facilidade de escrita, confiabilidade e custo.
- **Legibilidade (Readability):** Refere-se à facilidade com que um programa pode ser lido e compreendido. Este é um fator crítico para a manutenção do software. A legibilidade é influenciada por:
	- **Simplicidade:** Uma linguagem com um número menor de conceitos básicos e construções é mais fácil de aprender e ler. A multiplicidade de recursos (várias maneiras de realizar a mesma tarefa) e a sobrecarga excessiva de operadores podem prejudicar a simplicidade.
	- **Ortogonalidade:** É a propriedade de uma linguagem de programação que permite que suas características sejam combinadas de forma consistente e sem regras especiais ou exceções, tornando-a mais simples e previsível.
	- **Tipos de Dados:** A presença de tipos de dados adequados, como um tipo booleano nativo em vez de usar inteiros (ex.: 1 para true), melhora a clareza do código.
	- **Projeto de Sintaxe:** O formato dos identificadores, o uso de palavras-chave significativas e a forma como os blocos de código são delimitados (ex.: chaves {} em C/Java versus indentação em Python) têm um impacto direto na legibilidade.
- **Facilidade de Escrita (Writability):** Mede a facilidade com que um programador pode usar a linguagem para criar programas para um domínio de problema específico. É afetada por:
	- **Simplicidade e Ortogonalidade:** Assim como na legibilidade, um conjunto pequeno e consistente de regras facilita a escrita de código correto.
	- **Expressividade:** Refere-se à disponibilidade de construções convenientes para especificar operações complexas de forma concisa. Por exemplo, a presença de um laço for em muitas linguagens simplifica a iteração sobre coleções de dados.
- **Confiabilidade (Reliability):** Um programa é confiável se ele se comporta de acordo com suas especificações sob todas as condições. Fatores que contribuem para a confiabilidade incluem:
	- **Verificação de Tipos:** A capacidade de detectar erros de tipo, preferencialmente em tempo de compilação (verificação estática), é crucial. Linguagens que adiam essa verificação para o tempo de execução (verificação dinâmica) podem permitir que erros passem despercebidos até que o programa esteja em produção.
	- **Tratamento de Exceções:** A habilidade de interceptar e gerenciar erros em tempo de execução (como divisões por zero ou falhas de I/O) de forma controlada, sem que o programa termine abruptamente, é fundamental em linguagens modernas como Java e C#.
	- **Apelidos (Aliasing):** A existência de duas ou mais referências distintas para a mesma localização de memória pode levar a efeitos colaterais inesperados e difíceis de depurar, reduzindo a confiabilidade.
- **Custo (Cost):** O custo total de uma linguagem de programação vai além do preço de seu compilador. Ele engloba o custo de treinamento de programadores, o tempo de desenvolvimento, a eficiência da compilação e da execução, e, mais importante, o custo de manutenção ao longo do tempo. Uma linguagem de baixa confiabilidade pode levar a custos altíssimos devido a falhas em sistemas críticos.
É importante notar que esses critérios frequentemente entram em conflito, representando trade-offs fundamentais no projeto de linguagens. Por exemplo, a linguagem C++ oferece ponteiros, que aumentam a flexibilidade e a facilidade de escrita para programação de sistemas de baixo nível, mas o fazem ao custo da confiabilidade, pois o gerenciamento manual de memória é uma fonte comum de erros graves. Em contraste, Java eliminou ponteiros explícitos, uma decisão de projeto que prioriza a confiabilidade e a segurança em detrimento do controle de baixo nível, tornando-a mais adequada para aplicações empresariais e web.
##### Influências no Projeto de Linguagens
O design de uma linguagem de programação não ocorre no vácuo; é profundamente influenciado por dois fatores principais: a arquitetura de hardware subjacente e as metodologias de desenvolvimento de software predominantes na época.
- **Arquitetura de von Neumann:** A vasta maioria dos computadores hoje segue a arquitetura de von Neumann, caracterizada por uma unidade de processamento central (CPU) separada de uma memória onde tanto os dados quanto as instruções do programa são armazenados. As instruções e os dados devem ser transferidos da memória para a CPU para serem processados. Esta arquitetura impôs um modelo computacional que se reflete diretamente nas linguagens imperativas:
	- **Variáveis** são abstrações das células de memória.
	- **Comandos de atribuição** modelam o movimento de dados da memória para a CPU e de volta.
	- **Iteração** (laços for, while) é a estrutura de controle mais natural e eficiente, pois otimiza a execução sequencial de instruções armazenadas em locais de memória contíguos.
Essa dependência da transferência de dados entre CPU e memória cria o que é conhecido como "Gargalo de von Neumann": a velocidade de conexão entre a memória e o processador limita a velocidade geral do computador, pois a CPU muitas vezes pode processar dados mais rápido do que eles podem ser buscados. Historicamente, esse gargalo tornou a eficiência da máquina a principal preocupação, favorecendo linguagens que ofereciam controle de baixo nível sobre o hardware, como C.
- **Metodologias de Programação:** A evolução das práticas de desenvolvimento de software também tem sido um motor para a inovação em linguagens.
	- Nas décadas de $1950$ e $1960$, o foco era a eficiência da máquina.
	- No final dos anos $1960$, com o aumento da complexidade do software, a eficiência do programador tornou-se importante, levando ao surgimento da programação estruturada. Essa metodologia, que enfatiza o uso de estruturas de controle como if-then-else e laços em vez de goto, influenciou fortemente linguagens como Pascal e C.
	- Na década de $1970$, o foco mudou de processos para dados, dando origem à abstração de dados, onde os detalhes de implementação de um tipo de dados são ocultados de seus usuários.
	- Finalmente, em meados da década de $1980$, a programação orientada a objetos (POO) combinou a abstração de dados com os conceitos de herança e polimorfismo, levando ao desenvolvimento de linguagens como C++ e, posteriormente, Java.
##### Métodos de Implementação
Para que um programa escrito em uma linguagem de alto nível seja executado por um computador, ele deve ser traduzido para a linguagem de máquina que o hardware entende. Existem três abordagens principais para essa tradução.
- **Compilação:** Um programa chamado compilador traduz todo o código-fonte em um arquivo executável de linguagem de máquina antes que o programa seja executado. O processo de compilação envolve várias fases:
	- **Análise Léxica**
	- **Análise Sintática**
	- **Análise Semântica**
	- **Geração de Código Intermediário**
- **Interpretação Pura:** Um programa chamado interpretador lê e executa o código-fonte instrução por instrução, sem uma fase de tradução prévia. A vantagem é a simplicidade e a flexibilidade, facilitando a depuração, pois os erros são relatados no contexto do código-fonte original. A grande desvantagem é o desempenho, pois cada instrução deve ser reanalisada toda vez que é executada.
- **Sistemas Híbridos:** Esta abordagem busca combinar as vantagens da compilação e da interpretação. O código-fonte é compilado para uma linguagem intermediária, que é mais fácil e rápida de interpretar do que a linguagem de alto nível original.
### Estrutura Formal das Linguagens
##### Definições Fundamentais:
- **Sintaxe:** É o conjunto de regras que ditam a forma das expressões, sentenças e unidades de programa. Ela define quais sequências de símbolos são programas estruturalmente válidos. Por exemplo, a sintaxe de um comando while em Java é `while (expressão_booleana) sentença.`
- **Semântica:** É o significado associado a essas estruturas sintaticamente válidas. Para o comando while, a semântica é que a sentença será executada repetidamente enquanto a `expressão_booleana` for verdadeira.
O primeiro passo para analisar a sintaxe de um programa é a análise léxica, que divide o código em seus componentes fundamentais:
- **Lexema:** É a menor sequência de caracteres em um programa que é tratada como uma unidade. Por exemplo, na expressão `index = 2 * count;`, os lexemas são `index`, `=`, `2`, `*`, `count` e `;`.
- **Token:** É a categoria ou tipo de um lexema. No mesmo exemplo, `index` e `count` são tokens do tipo identificador, `2` é um literal inteiro, e `*` é um operador de multiplicação.
##### Gramáticas Livres de Contexto e BNF
A sintaxe da maioria das linguagens de programação é formalmente definida por uma **Gramática Livre de Contexto (GLC)**. Uma gramática atua como um gerador, um conjunto de regras que pode produzir todas as sentenças válidas (e apenas as válidas) de uma linguagem.
A notação padrão para descrever essas gramáticas é a **Forma de Backus-Naur (BNF)**, uma metalinguagem (uma linguagem usada para descrever outras linguagens). Uma gramática BNF consiste em:
- **Símbolos Terminais:** Os tokens da linguagem (if, +, identificador).
- **Símbolos Não-Terminais:** Abstrações sintáticas que representam conjuntos de cadeias ($<stmt>$, $<expr>$).
- Regras: Especificam como um não-terminal pode ser substituído por uma sequência de terminais e/ou não-terminais. A forma geral é `<S> -> W`, onde `<S>` é o não-terminal do lado esquerdo (LHS) e `W` é a sequência do lado direito (RHS). Exemplo:
	- `<assign> -> <id> = <expr>`
	- `<id> -> A | B | C`
	- `<expr> -> <expr> + <term> | <term>`
##### Derivações e Árvores de Análise Sintática (Parse Trees)
Uma **derivação** é o processo de aplicar sucessivamente as regras de uma gramática, começando pelo símbolo inicial, para gerar uma sentença. 
A **Árvore de Análise Sintática** (Parse Tree) é uma representação gráfica hierárquica de uma derivação. Ela mostra visualmente como uma sentença é estruturada de acordo com a gramática.
- O nó raiz é o símbolo inicial da gramática.
- Cada nó interno é um símbolo não-terminal.
- Cada nó folha é um símbolo terminal.
##### Ambiguidade, Precedência e Associatividade
Uma gramática é ambígua se ela pode gerar duas ou more árvores de análise sintática distintas para a mesma sentença.
Exemplo de gramática ambígua:
`<expr> -> <expr> + <expr> | <expr> * <expr> | <id>`
Para a sentença `A = B + C * A`, esta gramática permite duas árvores: uma que agrupa `(B + C) * A` e outra que agrupa `B + (C * A)`. Cada uma levaria a um resultado numérico diferente, tornando a gramática inútil para um compilador.
A ambiguidade em gramáticas de expressão é resolvida **reescrevendo as regras** para impor a **precedência** e a **associatividade** dos operadores.
- Precedência: Define qual operador é avaliado primeiro em uma expressão com operadores diferentes (`*` tem maior precedência que `+`). Para impor isso na gramática, são criados múltiplos não-terminais, um para cada nível de precedência. Por exemplo:
	- `<expr> -> <expr> + <term> | <term>`
	- `<term> -> <term> * <factor> | <factor>`
	- `<factor> -> (<expr>) | <id>`
- **Associatividade:** Define a ordem de avaliação para operadores com a mesma precedência (`A - B - C` é `(A - B) - C`). A associatividade é controlada pela recursão nas regras gramaticais.
	- **Recursão à esquerda:** `<expr> -> <expr> - <term>` gera associatividade à esquerda.
	- **Recursão à direita:** `<factor> -> <expr> ** <factor>` gera associatividade à direita, comum para operadores de exponenciação.
#####  EBNF (Extended Backus-Naur Form)
A EBNF é uma variação da BNF que adiciona notações para tornar as gramáticas mais concisas e legíveis, sem aumentar seu poder descritivo. Suas principais extensões são:
- Colchetes `[...]` para partes opcionais:
	- EBNF: `<if_stmt> -> if (<expr>) <stmt> [else <stmt>]` 
	- Isso substitui duas regras BNF, uma com a parte else e outra sem.
- Chaves `{...}` para repetição:
	- EBNF: `<ident_list> -> <identifier> {, <identifier>}`
	- Isso substitui uma regra BNF recursiva para descrever uma lista de identificadores separados por vírgula.
- Parênteses `(...)` para agrupamento de escolhas:
	- EBNF: `<term> -> <factor> {(* | /) <factor>}`
	- Isso agrupa os operadores `*` e `/`, indicando que qualquer um deles pode ser usado na repetição.
### Nomes, Vinculações, Escopo e Tempo de Vida
##### Atributos de uma Variável:
Uma variável, a abstração fundamental de uma célula de memória em linguagens imperativas, é caracterizada por seis atributos principais:
- **Nome:** O identificador usado para se referir à variável.
- **Endereço:** A localização na memória onde o valor da variável está armazenado.
- **Tipo:** Define o conjunto de valores que a variável pode armazenar e as operações que podem ser aplicadas a ela.
- **Valor:** O conteúdo da célula de memória associada.
- **Tempo de Vida:** O período de tempo durante a execução do programa em que a variável está vinculada a um endereço de memória.
- **Escopo:** A região do código-fonte na qual a variável é visível e pode ser referenciada pelo seu nome.
##### Vinculação:
É o processo de associar um atributo a uma entidade, como vincular um tipo a uma variável ou um símbolo de operação (+) à sua implementação. O momento em que essa associação ocorre é o tempo de vinculação. As vinculações podem ser classificadas como estáticas ou dinâmicas.
- **Vinculação Estática:** Ocorre antes do tempo de execução e permanece fixa durante toda a execução do programa. É mais eficiente e permite a detecção de erros em tempo de compilação. A vinculação de tipos estática é a norma em linguagens como C, Java e C#. Ela pode ser:
	- **Explícita:** O tipo é declarado pelo programador.
	- **Implícita:** O tipo é inferido pelo compilador com base no valor inicial.
- **Vinculação Dinâmica:** Ocorre durante o tempo de execução e pode mudar. É mais flexível, mas menos eficiente e mais propensa a erros de tipo que só são detectados em tempo de execução. A vinculação de tipos dinâmica é característica de linguagens de script como JavaScript e Python, onde uma variável pode ser vinculada a um inteiro em um momento e a uma string em outro.
A escolha entre paradigmas estáticos e dinâmicos representa um trade-off filosófico central no projeto de linguagens. A abordagem estática prioriza a segurança, a previsibilidade e a eficiência em tempo de compilação. A abordagem dinâmica prioriza a flexibilidade, a expressividade e a prototipagem rápida em tempo de execução.
##### Tempo de Vida:
O tempo de vida de uma variável é determinado por quando a memória é alocada e liberada para ela. Existem quatro categorias principais:
- **Estáticas:** A memória é alocada no início da execução do programa e permanece alocada até o término. Variáveis *globais* e variáveis *locais* declaradas com *static* em C/C++ se enquadram nesta categoria. São eficientes, mas inflexíveis e não suportam recursão adequadamente.
- **Dinâmicas de Pilha:** A memória é alocada na pilha de execução quando o bloco de declaração é ativado e é liberada automaticamente quando o bloco termina. Este é o método padrão para variáveis locais em C, C++, Java, etc. Ele suporta recursão de forma eficiente, mas incorre em uma pequena sobrecarga de alocação/liberação a cada chamada de função.
- **Dinâmicas de Monte Explícitas:** A memória é alocada e liberada do monte por instruções explícitas do programador (*malloc* e *free* em C). Isso oferece grande flexibilidade para criar estruturas de dados complexas cujo tamanho não é conhecido em tempo de compilação, mas transfere a responsabilidade do gerenciamento de memória para o programador, criando o risco de vazamentos de memória e ponteiros pendentes.
##### Escopo:
O escopo de uma variável define onde no texto do programa ela pode ser referenciada. As regras de escopo determinam como uma referência a um nome é associada à sua declaração, especialmente para variáveis não locais (visíveis em um bloco, mas declaradas em outro).
- **Escopo Estático (ou Léxico):** As associações de nomes são determinadas pela estrutura textual do programa em tempo de compilação. A busca por uma variável não local começa no escopo atual e prossegue para os escopos que o contêm textualmente (o "pai estático", o "avô estático", etc.) até que uma declaração seja encontrada ou o escopo global seja alcançado. Uma variável declarada em um escopo interno pode ocultar uma variável com o mesmo nome em um escopo externo.
- **Escopo Dinâmico:** As associações de nomes são baseadas na sequência de chamadas de função em tempo de execução. A busca por uma variável não local começa na função atual e prossegue pela cadeia de chamadas (a função que a chamou, a função que chamou aquela, e assim por diante, subindo na pilha de chamadas). O significado de uma variável não local depende de quem chamou a função. Embora conveniente em alguns cenários, o escopo dinâmico torna os programas difíceis de ler e raciocinar, pois as ligações não são aparentes no código-fonte, e impede a verificação de tipos estática.
### Sistemas de Tipos e Estruturas de Dados
##### Tipos de Dados Primitivos:
Um tipo de dado define uma coleção de valores e um conjunto de operações predefinidas sobre esses valores.1 Os tipos primitivos são aqueles não definidos em termos de outros tipos e geralmente refletem o suporte do hardware.
- **Inteiro:** O tipo numérico mais comum.
- **Ponto Flutuante:** Modelam números reais como aproximações.
- **Decimal:** Usados em aplicações financeiras para representar valores decimais com precisão, evitando os erros de arredondamento do ponto flutuante binário. Geralmente usam representação BCD (Binary Coded Decimal).
- **Booleano:** O tipo mais simples, com valores true e false.
- **Caractere:** Armazenados como códigos numéricos. As codificações evoluíram do ASCII (8 bits) para o Unicode, que suporta caracteres de praticamente todos os idiomas do mundo.
##### Cadeias de Caracteres (Strings):
Strings são sequências de caracteres. As implementações variam:
- **Estáticas:** O comprimento é fixo e conhecido em tempo de compilação. (*strings imutáveis em Java*)
- **Dinâmicas de Tamanho Limitado:** O comprimento pode variar até um máximo predefinido. (*vetor de char em C*)
- **Dinâmicas:** O comprimento pode variar sem limite, exigindo gerenciamento de memória no monte. (*strings em JavaScript*)
##### Tipos Estruturados (Matrizes):
Uma matriz é um agregado homogêneo de elementos de dados, onde cada elemento é acessado por sua posição (índice).
- **Alocação de Memória:** Assim como as variáveis, as matrizes podem ser alocadas de diferentes maneiras, cada uma com suas próprias implicações de desempenho e flexibilidade.

| Categoria              | Vinculação de Armaz.  | Vantagens                                                                     | Desvantagens                                                       | Exemplo                                          |
| ---------------------- | --------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------ |
| Estática               | Estática (compilação) | Eficiência máxima (sem alocação em tempo de execução).                        | Inflexível; memória alocada durante toda a execução.               | Variáveis globais em C/C++ ou static em funções. |
| Dinâmica de Pilha Fixa | Estática (compilação) | Uso eficiente de espaço (memória liberada no fim do bloco); suporta recursão. | Sobrecarga de alocação/liberação; risco de estouro de pilha.       | Variáveis locais de matriz em C/C++.             |
| Dinâmica do Monte Fixa | Dinâmica (execução)   | Flexível no tamanho (definido em tempo de execução).                          | O tamanho é fixo após a alocação; custo do gerenciamento do monte. | Arrays em Java (new int[size]); malloc em C.     |
| Dinâmica do Monte      | Dinâmica (execução)   | Máxima flexibilidade (pode crescer/encolher).<br>                             | Maior custo de gerenciamento e desempenho.                         | ArrayList em Java; listas em Python.             |
- **Mapeamento de Endereços:** Como a memória do computador é linear, matrizes multidimensionais precisam ser mapeadas para um vetor unidimensional. A maioria das linguagens (C, C++, Java, Python) usa a ordem principal de linha (row-major order), onde as linhas adjacentes são armazenadas contiguamente. Fortran usa a ordem principal de coluna (column-major order). A fórmula para calcular o endereço de um elemento `A[i][j]` em uma matriz `m` x `n` em row-major order, com índice base 0, é: `endereço(A[i][j]) = endereço_base + (i * n + j) * tamanho_elemento`.
- **Matrizes Irregulares:** São matrizes multidimensionais onde as linhas podem ter comprimentos diferentes. São possíveis em linguagens que implementam matrizes multidimensionais como "vetores de vetores".
- **Operações:** Linguagens de alto nível como Python e Fortran fornecem operações de matriz inteira, como atribuição, concatenação e fatiamento, que permite referenciar uma subestrutura da matriz de forma conveniente.
##### Matrizes Associativas e Registros:
- **Matrizes Associativas:** São coleções não ordenadas de elementos indexados por chaves definidas pelo usuário, em vez de índices numéricos. São conhecidas como dicionários em Python. São estruturas de dados extremamente flexíveis e eficientes para buscas baseadas em chaves, geralmente implementadas com tabelas de hash.
- **Registros (Structs/Records):** São agregados de elementos de dados possivelmente heterogêneos, onde cada elemento (ou campo) é identificado por um nome, não por um índice. Ao contrário das matrizes heterogêneas de linguagens de script (onde os elementos são referências espalhadas no monte), os campos de um registro são tipicamente armazenados em locais de memória contíguos, permitindo acesso eficiente por meio de um deslocamento (offset) a partir do endereço base do registro.
##### Sistemas de Tipos:
- **Verificação de Tipos:** É o processo de garantir que os operandos de um operador sejam de tipos compatíveis.
	- **Verificação Estática:** Realizada em tempo de compilação. É mais segura, pois detecta erros mais cedo.
	- **Verificação Dinâmica:** Realizada em tempo de execução. É mais flexível, mas os erros de tipo só se manifestam quando o código é executado.
- **Tipagem Forte:** Uma linguagem é fortemente tipada se erros de tipo são sempre detectados, seja em tempo de compilação ou de execução. Isso impede que uma operação seja aplicada a um objeto de um tipo inadequado. Python, por exemplo, é dinamicamente tipado, mas fortemente tipado: uma tentativa de somar um número e uma string ("10" + 5) resultará em um *TypeError* em tempo de execução, em vez de produzir um resultado inesperado. Em contraste, C e C++ não são fortemente tipados devido a recursos como unions e coerções explícitas que podem subverter o sistema de tipos.
- **Coerção:** É a conversão implícita (automática) de um tipo para outro, como quando um int é adicionado a um float em C. Embora conveniente, coerções excessivas podem mascarar erros de programação e enfraquecer a tipagem forte.
- **Equivalência de Tipos:** Determina se dois tipos são considerados os mesmos.
	- **Equivalência por Nome:** Dois tipos são equivalentes apenas se tiverem o mesmo nome de tipo. É mais rigorosa e pode capturar erros semânticos. Por exemplo, dois tipos Celsius e Fahrenheit, ambos definidos como float, não seriam equivalentes, impedindo atribuições acidentais entre eles.
	- **Equivalência por Estrutura:** Dois tipos são equivalentes se tiverem a mesma estrutura interna, independentemente de seus nomes. É mais flexível, mas pode ser menos segura, pois trataria os tipos Celsius e Fahrenheit do exemplo anterior como equivalentes.
# 2º GQ
### Materiais de Apoio:
- [[Paradigmas - Aula 06 - Expressões e Sentenças de Atribuição.pdf]]
- [[Paradigmas - Aula 07 - Estruturas de Controle no Nível de Sentença.pdf]]
- [[Paradigmas - Aula 08 - Subprogramas.pdf]]
- [[Paradigmas - Aula 09 - Exceções.pdf]]
- [[Paradigmas - Aula 10 - Programação Orientada a Objetos.pdf]]
- [[Paradigmas - Aula 12 - Programação Funcional.pdf]]
- [[Paradigmas - Aula 13 - Programação Lógica.pdf]]
### Resumo:
- [[Paradigmas - Resumo 2GQ.pdf]]
- [[Paradigmas - Resumo 2GQ (Ana Bia).pdf]]
