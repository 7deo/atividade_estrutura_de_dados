# Relatório — Atividade Avaliativa de Estruturas de Dados

**Alunos:** Jorge Luis Soares Dos Santos e Felipe Falcão Campelo | **Curso:** Engenharia de Software — UDF | **Valor:** 1,0 ponto
 Turma :D2
 

            
## Parte 1 — Pesquisa: Bubble Sort e Quick Sort

### Bubble Sort

**Como funciona:**
- Percorre o array repetidamente comparando pares de elementos adjacentes.
- Sempre que um par está fora de ordem, os dois elementos são trocados de posição.
- A cada passagem completa, o maior valor ainda não ordenado "flutua" até sua posição final.
- O processo se repete até que uma passagem inteira não realize nenhuma troca.
- Estrutura: dois laços aninhados — o externo controla o número de passagens, o interno compara e troca elementos adjacentes.

**Complexidade:**
- Melhor caso: O(n) — array já ordenado, com flag de parada antecipada ("swapped").
- Caso médio: O(n²).
- Pior caso: O(n²) — array em ordem totalmente inversa.

**Vantagens:** implementação simples e intuitiva; estável; ordena in-place (O(1) de espaço extra); eficiente em arrays quase ordenados com a otimização de parada antecipada.

**Limitações:** ineficiente para grandes volumes, devido ao crescimento quadrático.

**Adequado para:** conjuntos pequenos, fins didáticos, dados quase ordenados.
**Não recomendado para:** grandes volumes ou aplicações onde desempenho é crítico.

### Quick Sort

**Como funciona:**
- Estratégia "dividir para conquistar".
- Escolhe um pivô (primeiro, último, meio ou aleatório).
- Particiona o array: menores que o pivô de um lado, maiores do outro; o pivô fica em sua posição definitiva.
- Aplica o processo recursivamente às duas sublistas até restarem 0 ou 1 elemento.

**Complexidade:**
- Melhor caso: O(n log n) — pivô sempre divide o array em metades aproximadamente iguais.
- Caso médio: O(n log n).
- Pior caso: O(n²) — escolha de pivô sistematicamente ruim (ex.: array já ordenado, pivô no extremo).

**Vantagens:** muito rápido na prática para grandes volumes; in-place com O(log n) de memória extra (pilha de recursão); base de implementações de ordenação em diversas linguagens/bibliotecas.

**Limitações:** pode degradar para O(n²) com pivô mal escolhido; não é estável; recursão pode estourar pilha em casos patológicos.

**Adequado para:** grandes volumes de dados, desempenho crítico.
**Não recomendado para:** quando estabilidade é exigida ou quando não é possível aleatorizar o pivô em dados quase ordenados.

### Tabela comparativa

| Característica | Bubble Sort | Quick Sort |
|---|---|---|
| Princípio | Comparação e troca de elementos adjacentes | Divisão e conquista com particionamento em torno de um pivô |
| Melhor caso | O(n) | O(n log n) |
| Caso médio | O(n²) | O(n log n) |
| Pior caso | O(n²) | O(n²) |
| Uso de memória | O(1) — in-place | O(log n) — pilha de recursão |
| Vantagem principal | Simplicidade | Alta eficiência em grandes volumes |
| Limitação principal | Ineficiente para grandes entradas | Pior caso quadrático com pivô mal escolhido |
| Aplicação recomendada | Ensino, arrays pequenos/quase ordenados | Ordenação de grandes conjuntos |

## Parte 2 — Experimento de Ordenação

Código em [`bubble_sort.py`](bubble_sort.py), [`quick_sort.py`](quick_sort.py) e [`comparacao.py`](comparacao.py). Os dois algoritmos foram instrumentados para contar comparações e trocas/movimentações, usando a mesma cópia dos dados aleatórios em cada tamanho testado.

**Resultados registrados (dados reais de execução):**

| Tamanho | Bubble — Comparações | Bubble — Trocas | Quick — Comparações | Quick — Movimentações |
|---|---|---|---|---|
| 10 | 45 | 26 | 29 | 10 |
| 20 | 187 | 114 | 62 | 40 |
| 1.000 | 499.329 | 241.624 | 10.695 | 5.144 |

**Tempos medidos (informativo, dependem do computador usado):**

| Tamanho | Bubble Sort (ms) | Quick Sort (ms) |
|---|---|---|
| 10 | 0,008 | 0,060 |
| 20 | 0,016 | 0,012 |
| 1.000 | 46,444 | 1,066 |

**Respostas:**

**a) Qual algoritmo realizou menos operações para 10 elementos?**
O Quick Sort: 39 operações no total (29 comparações + 10 movimentações) contra 71 do Bubble Sort (45 comparações + 26 trocas).

**b) O comportamento permaneceu igual para 20 elementos?**
Sim, o Quick Sort continuou realizando menos operações (102 no total) do que o Bubble Sort (301 no total), e a diferença relativa já começou a aumentar.

**c) O que aconteceu quando o tamanho aumentou para 1.000?**
A diferença se tornou drástica: o Bubble Sort realizou 740.953 operações no total, enquanto o Quick Sort realizou apenas 15.839 — quase 47 vezes menos.

**d) Qual algoritmo apresentou maior crescimento da quantidade de operações?**
O Bubble Sort, cujo número de operações cresce de forma quadrática (O(n²)) em relação ao tamanho da entrada.

**e) Os resultados experimentais são coerentes com as complexidades teóricas estudadas?**
Sim. O crescimento quase 500x nas comparações do Bubble Sort (de 45 para quase 500 mil) ao passar de n=10 para n=1.000 é compatível com O(n²); o crescimento muito mais moderado do Quick Sort é compatível com O(n log n).

**f) Em qual situação você escolheria Bubble Sort?**
Em conjuntos pequenos de dados, em contextos didáticos, ou quando os dados já estão quase ordenados e a simplicidade da implementação é mais importante que a performance.

**g) Em qual situação você escolheria Quick Sort?**
Em qualquer cenário com grandes volumes de dados e onde desempenho é um requisito relevante — é a escolha padrão para ordenação de propósito geral.

## Parte 3 — Investigação de Busca em Matrizes

Código em [`busca_sequencial.py`](busca_sequencial.py). Implementa busca sequencial com loops aninhados, percorrendo a matriz linha por linha e coluna por coluna.

**Resultados (número de comparações):**

| Matriz | Nº de elementos | Busca no início | Busca no final | Valor inexistente |
|---|---|---|---|---|
| 2 × 2 | 4 | 1 | 3 | 4 |
| 10 × 10 | 100 | 1 | 99 | 100 |
| 100 × 100 | 10.000 | 1 | 9.999 | 10.000 |

**Respostas:**

**a) Por que encontrar um elemento no início exige menos operações?**
Porque a busca percorre a matriz na ordem em que os elementos foram organizados (linha a linha); se o valor está na primeira posição, apenas uma comparação é necessária antes que o algoritmo encontre e interrompa a busca.

**b) O que acontece quando o elemento procurado não existe?**
O algoritmo percorre todas as posições da matriz, sem interrupção antecipada, realizando o número máximo possível de comparações (linhas × colunas).

**c) Qual é o pior caso da busca sequencial?**
Ocorre quando o valor está na última posição verificada ou é inexistente — em ambos os casos, todas as m × n posições precisam ser comparadas.

**d) Como o aumento das dimensões da matriz influencia a quantidade de operações?**
O número máximo de comparações cresce proporcionalmente ao total de elementos (linhas × colunas); de 10×10 para 100×100, o número de elementos (e o pior caso) cresce de 100 para 10.000 — cem vezes mais.

**e) Qual a complexidade da busca sequencial em uma matriz m × n?**
O(m × n) — complexidade linear em relação ao número total de elementos da matriz.

## Parte 4 — Hands On 1: Investigação do Array

Código em [`temperaturas.py`](temperaturas.py). Array de 10 temperaturas, processado para calcular média, maior/menor valor (com índices) e quantidade de valores acima da média.

**Resultado da execução:**

| Índice | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| Temp. (°C) | 19,9 | 17,3 | 24,8 | 16,1 | 23,0 | 20,5 | 15,9 | 22,6 | 15,6 | 21,5 |

- Média: 19,72 °C
- Maior valor: 24,8 °C — índice 2
- Menor valor: 15,6 °C — índice 8
- Valores acima da média: 6

**Análise de operações e complexidade:**
O algoritmo realiza 4 percursos completos sobre o array de n elementos: (1) acumular a soma, (2) verificar maior/menor, (3) exibir os elementos e (4) contar quantos valores estão acima da média. Cada percurso realiza n operações, logo:

T(n) = 4n → para n = 10, T(10) = 40 operações (valor confirmado na execução do código instrumentado).

Como a constante 4 é desprezada na notação Big-O, a complexidade do algoritmo é **O(n)** — crescimento linear em relação ao tamanho do array.

## Parte 5 — Hands On 2: Matriz Aplicada — Monitoramento de Sensores

Código em [`sensores.py`](sensores.py). Matriz 5 × 24 (5 sensores × 24 medições/hora), usada para calcular médias por sensor, maior temperatura registrada (com sensor e horário), média geral e quantidade de leituras acima de um limite informado.

**Resultado da execução (limite = 28,0 °C):**

| Sensor 0 | Sensor 1 | Sensor 2 | Sensor 3 | Sensor 4 |
|---|---|---|---|---|
| 23,80 °C | 24,06 °C | 23,59 °C | 23,41 °C | 24,28 °C |

- Maior temperatura registrada: 30,0 °C
- Sensor responsável: Sensor 1
- Horário da ocorrência: 12h
- Média geral (das 120 medições): 23,83 °C
- Leituras acima de 28,0 °C: 23

**Análise final:**

- **Por que são necessários loops aninhados:** a matriz tem duas dimensões (sensores e horários); um único loop percorreria apenas uma linha ou coluna. O loop externo percorre cada sensor (linha) e o interno percorre cada horário (coluna) daquele sensor, garantindo que todas as 5 × 24 = 120 medições sejam visitadas.
- **Papel dos índices [i][j]:** i identifica o sensor (linha) e j identifica o horário, de 0 a 23 (coluna). Juntos, `sensores[i][j]` localizam exatamente uma medição específica.
- **Quantas posições são percorridas:** todas as 120 posições (5 sensores × 24 horários), exatamente uma vez.
- **Relação entre linhas, colunas e operações:** o número de operações é proporcional ao produto do número de linhas pelo número de colunas — T(m, n) = k × m × n, complexidade O(m × n).

## Parte 6 — Análise e Conclusão

**1. O aumento do tamanho da estrutura de dados influencia a quantidade de operações?**
Sim. Em todos os experimentos — ordenação, busca em matriz e os dois Hands On — o número de operações cresceu junto com o tamanho da entrada. A taxa de crescimento, porém, depende da complexidade do algoritmo: quadrática no Bubble Sort, linear (ou próxima disso) no Quick Sort e nos algoritmos de percurso linear.

**2. Bubble Sort e Quick Sort crescem da mesma maneira quando o número de elementos aumenta?**
Não. O Bubble Sort tem complexidade O(n²): ao multiplicar a entrada por 100 (de 10 para 1.000), o número de comparações cresceu cerca de 11.000 vezes (de 45 para quase 500 mil). O Quick Sort, com O(n log n), teve crescimento muito mais moderado no mesmo intervalo (de 29 para cerca de 10.700 comparações). Essa diferença, imperceptível em arrays pequenos, torna-se decisiva conforme os dados aumentam.

**3. Por que analisar somente o resultado final da ordenação não é suficiente para comparar algoritmos?**
Porque o resultado final — o array ordenado — é idêntico para os dois algoritmos, mas o caminho até chegar a esse resultado (comparações, trocas, movimentações) pode ser radicalmente diferente. Observar apenas o resultado esconde informações essenciais sobre eficiência e escalabilidade: um algoritmo pode ser inviável para grandes volumes mesmo produzindo o resultado correto, e isso só fica evidente ao medir e comparar a complexidade computacional de cada algoritmo.

### Conclusão geral

Os experimentos confirmaram, na prática, que o tamanho da entrada e o algoritmo escolhido determinam juntos o custo computacional de uma tarefa. Estruturas simples como arrays e matrizes oferecem acesso rápido e direto (O(1)) às suas posições, mas operações que exigem percorrer todos os elementos (busca, soma, comparação) têm custo proporcional ao tamanho da estrutura — O(n) em arrays e O(m × n) em matrizes. Entre os algoritmos de ordenação, o experimento evidenciou de forma clara a diferença entre O(n²) e O(n log n): para entradas pequenas essa diferença é discreta, mas para entradas maiores ela se torna o fator determinante na viabilidade do algoritmo. A relação central trabalhada em toda a atividade — tamanho da entrada → número de operações → complexidade → eficiência do algoritmo — é, portanto, o critério correto para comparar algoritmos, e não apenas a corretude do resultado final.
