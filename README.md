
# 📦 Análise Experimental de Algoritmos — Problema da Mochila 0/1 (Logistech)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab&logoColor=white)
![IFCE](https://img.shields.io/badge/IFCE-PPGCC%202026.2-006633)

Estudo experimental comparativo entre três paradigmas algorítmicos aplicados à resolução do **Problema da Mochila 0/1** (*0/1 Knapsack Problem* — Tema 7.10: Logistech), desenvolvido na disciplina de **Projeto e Análise de Algoritmos (2026.2)** do Programa de Pós-Graduação em Ciência da Computação (**PPGCC — IFCE**).

---

## 🎯 Objetivo

Avaliar empiricamente o impacto do crescimento do tamanho da entrada ($n$) e da capacidade do veículo ($W$) sobre o **tempo médio de execução** e a **otimalidade das soluções** obtidas por três estratégias distintas:

| Abordagem | Estratégia | Complexidade de Tempo | Garante Solução Ótima? |
| :--- | :--- | :---: | :---: |
| **Algoritmo Guloso Ingênuo** | Ordenação decrescente pela razão $\text{valor}/\text{peso}$ | $O(n \log n)$ | ❌ Não |
| **Força-Bruta Ingênuo** | Busca exaustiva em todos os subconjuntos (*bitmask*) | $O(2^n)$ | ✅ Sim |
| **Programação Dinâmica** | Tabela *Bottom-Up* com reconstrução via *backtracking* | $O(n \cdot W)$ | ✅ Sim |

> **Nota:** A implementação de Programação Dinâmica retorna tanto o **valor máximo transportado** quanto o **subconjunto exato de itens selecionados** na solução ótima.

---

## 🧪 Metodologia Experimental

Para garantir rigor estatístico e comparação justa, todos os algoritmos foram executados sobre exatamente as mesmas instâncias geradas aleatoriamente (`random.seed(42)`), com **10 execuções distintas por tamanho de entrada** para cálculo do tempo médio (`time.perf_counter()`):

1. **Experimento 1 — Comparação Geral ($n = 4$ a $20$):** Confronta os três algoritmos simultaneamente para evidenciar a explosão exponencial do Força-Bruta ($O(2^n)$) e validar via `assert` a concordância de 100% entre Força-Bruta e Programação Dinâmica.
2. **Experimento 2 — Escalabilidade ($100$ tamanhos até $n = 1000$, com $W = 10n$):** Avalia o crescimento quadrático $O(n^2)$ da Programação Dinâmica frente ao comportamento quase plano do Algoritmo Guloso ($O(n \log n)$), mensurando a média e o desvio padrão do ganho de otimalidade da PD.
3. **Experimento 3 — Impacto da Capacidade ($W = 100$ a $5000$, com $n = 200$ fixo):** Isola a segunda dimensão do problema para demonstrar o crescimento linear $O(W)$ da Programação Dinâmica em contraste com a independência de $W$ na heurística gulosa.

---

## 📊 Principais Resultados

* **Validação de Corretude:** Em todas as **1.000 instâncias** testadas na etapa de escalabilidade, a Programação Dinâmica superou ou igualou o valor obtido pelo Algoritmo Guloso (`val_pd >= val_g`).
* **Qualidade da Solução (PD vs. Guloso):**
  * **Ganho Absoluto:** Média de **$4,45$** unidades de valor (Desvio Padrão: **$4,32$**).
  * **Ganho Percentual:** Média de **$0,06\%$** (Desvio Padrão: **$0,30\%$**).
* **Trade-off Prático:** Enquanto o Força-Bruta torna-se inviável já em $n = 20$ (~3.300 ms), a Programação Dinâmica resolve instâncias de $n = 1000$ ($W = 10.000$) em ~2,75 segundos entregando a solução exata, ao passo que o Guloso opera em frações de milissegundo como alternativa aproximada.

---

## 🔗 Links da Entrega

* 📓 **Notebook Interativo (Google Colab):** `https://colab.research.google.com/drive/1g6nioutGm9QtTUfVk7WuBaUK6GLkVGFH`
---

## 🚀 Como Executar Localmente

Caso deseje reproduzir os experimentos fora do Google Colab:

```bash
# 1. Clone este repositório
git clone https://github.com/Wesnei/experimento-PAA
cd experimento-PAA

# 2. Instale as dependências
pip install numpy matplotlib jupyter

# 3. Abra o notebook
jupyter notebook "experimento (PAA).ipynb"

```

---

## 👤 Autor

* **Discente:** Wesnei de Paiva Batista — Mestrando em Ciência da Computação (PPGCC / IFCE)
* **Docente:** Prof. Dr. Thiago Alves Rocha



