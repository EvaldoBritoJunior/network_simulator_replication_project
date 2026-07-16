# Network Simulator Replication Project

Este repositório contém o **Kit de Reprodução** do trabalho **"Simulação de Conversas em Redes Sociais com Modelos Baseados em Agentes Generativos: Um Estudo de Replicação"**.

**Artigo:**
https://drive.google.com/file/d/1N4-NnMlQ0xhJqQ6K6NDzNcIxR8QkN-9L/view?usp=drive_link

O trabalho apresenta uma replicação do estudo de Jeon et al., **"Simulating conversations on social media with generative agent-based models"**.

**Paper original:**
https://doi.org/10.1140/epjds/s13688-025-00593-3

O objetivo da replicação é reavaliar os resultados obtidos pelos autores, que propuseram um *framework* capaz de simular conversas em redes sociais a partir de notícias utilizando modelos baseados em agentes e Grandes Modelos de Linguagem (LLMs). Para isso, novas conversas foram geradas utilizando o *Network Simulator* disponibilizado por Jeon et al. e analisadas quanto à sua semelhança com conversas naturais e ao impacto da veracidade do conteúdo na dinâmica das discussões simuladas.

---

# Estrutura do Projeto

```
.
├── Notebooks
│   ├── network_simulator.ipynb
│   ├── simulated_conversations_analysis.ipynb
│   └── survey_results_analysis.ipynb
│
└── Data
    ├── Network Simulator
    │   ├── true_news_table.csv
    │   └── false_news_table.csv
    │
    ├── Simulated Conversations Analysis
    │   ├── Simulated Conversations
    │   └── Twitter16
    │
    └── Survey Results Analysis
        ├── survey_results.xlsx
        └── 60_sample_messages.csv
```

---

# Notebooks

## `network_simulator.ipynb`

Executa o *Network Simulator* para gerar conversas simuladas em redes sociais a partir de uma notícia inicial e seu texto complementar.

Além da geração das conversas, o notebook calcula automaticamente as métricas implementadas pela biblioteca **NELA (News Landscape)** e as características estruturais das conversas.

### Dados utilizados

* `Data/Network Simulator/true_news_table.csv`
* `Data/Network Simulator/false_news_table.csv`

### Resultado

* Arquivos CSV contendo as conversas simuladas.
* Arquivos CSV contendo as métricas calculadas para cada conversa.

---

## `simulated_conversations_analysis.ipynb`

Realiza o cálculo de métricas adicionais, análises estatísticas e gera as visualizações utilizadas na comparação entre conversas naturais e simuladas.

### Dados utilizados

* Conversas geradas pelo `network_simulator.ipynb`
* Dataset Twitter16

Localização:

* `Data/Simulated Conversations Analysis/Simulated Conversations`
* `Data/Simulated Conversations Analysis/Twitter16`

### Resultado

* Estatísticas descritivas
* Testes estatísticos
* Figuras utilizadas no artigo

---

## `survey_results_analysis.ipynb`

Analisa as respostas obtidas na avaliação humana (*survey*), realizando testes estatísticos e gerando as visualizações utilizadas no artigo.

### Dados utilizados

* `survey_results.xlsx`
* `60_sample_messages.csv`

### Resultado

* Estatísticas da survey
* Testes estatísticos
* Figuras utilizadas no artigo

---

# Dados

## Network Simulator

| Arquivo                | Descrição                                                     |
| ---------------------- | ------------------------------------------------------------------------------------------- |
| `true_news_table.csv`  | 31 notícias verdadeiras e seus textos complementares, utilizados como entrada do simulador. |
| `false_news_table.csv` | 31 notícias falsas e seus textos complementares, utilizadas como entrada do simulador.      |

## Simulated Conversations Analysis

| Diretório                 | Descrição                                                                             |
| ------------------------- | ------------------------------------------------------------------------------------- |
| `Simulated Conversations` | Conversas geradas pelo simulador.                                                     |
| `Twitter16`               | Dataset Twitter16 utilizado para comparação com conversas naturais.                   |

## Survey Answers Analysis

| Arquivo                  | Descrição                                                                             |
| ------------------------ | ------------------------------------------------------------------------------------- |
| `survey_results.xlsx`    | Respostas dos participantes da survey.                                                |
| `60_sample_messages.csv` | Conjunto das 60 mensagens avaliadas, juntamente com sua origem (natural ou simulada). |

---

# Passos para Reprodução

## 1. Geração das Conversas Simuladas

Execute o notebook:

```
network_simulator.ipynb
```

O notebook deve ser executado **62 vezes**, uma para cada par de "notícia inicial" e "texto complementar" presente nos arquivos `*_news_table.csv`.

As instruções para execução encontram-se no próprio notebook.

Ao final serão gerados:

* 62 arquivos contendo as conversas simuladas;
* 62 arquivos contendo as métricas calculadas.

Os arquivos gerados e utilizados neste trabalho já estão disponíveis em:

```
Data/Simulated Conversations Analysis/Simulated Conversations
```

---

## 2. Análise das Conversas Simuladas

Execute:

```
simulated_conversations_analysis.ipynb
```

Utilize:

* todas as conversas geradas na etapa anterior;
* o conjunto de dados Twitter16.

As instruções de execução encontram-se no notebook.

Ao final serão produzidos:

* métricas das conversas;
* análises estatísticas;
* gráficos e tabelas apresentados no artigo.

---

## 3. Análise da Survey

Execute:

```
survey_results_analysis.ipynb
```

Utilize:

* `survey_results.xlsx`
* `60_sample_messages.csv`

As instruções para execução encontram-se no notebook.

Ao final serão produzidos:

* análises estatísticas da survey;
* gráficos utilizados no artigo.
