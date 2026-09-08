# Atividade Avaliativa — Estruturas de Dados

**Aluno:** Jorge | **Curso:** Engenharia de Software — UDF

Arrays, matrizes e algoritmos de ordenação e busca (Bubble Sort, Quick
Sort e busca sequencial em matriz), com implementação, instrumentação
(contagem de comparações/trocas) e análise de complexidade.

O relatório completo com as respostas escritas está em [`RELATORIO.md`](RELATORIO.md).
O código está separado por parte do trabalho:

```
atividade-estruturas-de-dados/
├── RELATORIO.md              # respostas e análise (Partes 1, 3, 4, 5 e 6)
├── ordenacao/                # Parte 2 — experimento de ordenação
│   ├── bubble_sort.py
│   ├── quick_sort.py
│   └── comparacao.py         # roda os dois algoritmos sobre os mesmos dados
├── busca_matriz/              # Parte 3 — busca sequencial em matriz
│   └── busca_sequencial.py
├── hands_on_1_array/          # Parte 4 — investigação de array
│   └── temperaturas.py
└── hands_on_2_matriz/          # Parte 5 — matriz aplicada (sensores)
    └── sensores.py
```

## Como executar

Requer apenas Python 3 (sem dependências externas).

```bash
python3 ordenacao/bubble_sort.py
python3 ordenacao/quick_sort.py
cd ordenacao && python3 comparacao.py      # compara os dois no mesmo dataset
python3 busca_matriz/busca_sequencial.py
python3 hands_on_1_array/temperaturas.py
python3 hands_on_2_matriz/sensores.py
```

> Os números impressos por `comparacao.py` variam a cada execução (dados
> aleatórios). Os valores documentados no `RELATORIO.md` correspondem a
> uma execução específica registrada durante a atividade.
