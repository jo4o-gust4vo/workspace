
# 🎬 IMDb Analyst: Pipeline de ETL e BI para Cinema

![Status do Projeto](https://img.shields.io/badge/Status-Conclu%C3%ADdo-green)
![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Data%20Viz-yellow?logo=microsoft-power-bi&logoColor=black)
![Data Engineering](https://img.shields.io/badge/Pipeline-ETL%20%2F%20Modelagem-orange)

## 📌 Visão Geral do Projeto
Este projeto consiste no desenvolvimento de um pipeline completo de **Engenharia e Análise de Dados (BI)** utilizando os datasets oficiais e públicos do **IMDb**. O objetivo principal é extrair, filtrar, transformar e modelar um volume massivo de dados cinematográficos, realizando um recorte analítico específico focado na produção e no engajamento histórico de filmes.

O projeto cobre todo o ciclo de vida do dado: desde o consumo de arquivos brutos textuais em larga escala, passando pelo tratamento de dados via programação funcional, estruturação em tabelas analíticas (fatos e dimensões), até a entrega de valor através de um painel visual e interativo de suporte à decisão.

---

## 🏗️ Arquitetura do Pipeline (ETL)
O fluxo de dados segue uma arquitetura linear e desacoplada, garantindo que a extração e a modelagem precedam eficientemente o consumo visual:

```text
[Fontes do IMDb] ──> [Processamento em Python] ──> [Arquivos Estruturados] ──> [Consumo Visual]
 (title.*.tsv)          (Jupyter Notebooks)         (Tabelas Fato/CSV)          (Power BI)

```

1. **Extraction (Extração):** Ingestão dos arquivos oficiais descompactados do IMDb (`.tsv`), contendo dados brutos sobre títulos, avaliações, episódios e elencos principais.
2. **Transformation (Transformação & Modelagem):** Limpeza de dados nulos, padronização de tipos, cruzamento de chaves e filtragem utilizando **Python e Pandas**.
3. **Load (Carga):** Persistência dos dados processados em arquivos estruturados `.csv`, divididos entre visões cadastrais e tabelas fato/dimensão otimizadas para o modelo analítico.
4. **Data Visualization (Visualização):** Modelagem e cálculos de métricas no **Power BI** para geração de insights consolidados.

---

## 📂 Estrutura do Projeto

A árvore de diretórios está organizada seguindo as boas práticas de projetos de dados, separando o ambiente virtual, os dados brutos/tratados, os scripts de desenvolvimento e os entregáveis de BI:

```text
IMDB_ANALYST/
├── .venv/                     # Ambiente virtual Python (isolamento de dependências)
├── dashboard/
│   └── Dashboard.pbix         # Arquivo de modelagem e relatório do Power BI
├── datasets/                  # Repositório de dados do projeto
│   ├── filmes_brasileiros.csv          # Dados consolidados após processamento
│   ├── tb_fatos_filmes_brasileiros.csv # Tabela fato otimizada para o modelo estrela
│   ├── title.akas.tsv                  # Dados brutos: Títulos alternativos e regiões
│   ├── title.basics.tsv                # Dados brutos: Informações básicas de títulos
│   ├── title.episode.tsv               # Dados brutos: Vínculos de séries e episódios
│   ├── title.principals.tsv            # Dados brutos: Elenco e equipes principais
│   └── title.ratings.tsv               # Dados brutos: Votos e médias de avaliações
├── images/                    # Assets visuais da documentação e do dashboard
│   ├── Dashboard.png          # Screenshot do painel interativo
│   └── imdb_logo.png          # Identidade visual utilizada
├── notebooks/                 # Desenvolvimento dos scripts de Engenharia de Dados
│   ├── analise_de_dados_filmes_br.ipynb # Notebook focado no recorte principal e KPIs
│   └── exploracao_de_dados.ipynb        # Análise exploratória inicial das fontes brutas
├── .gitattributes
├── .gitignore                 # Configuração para ignorar arquivos locais pesados (.tsv/.venv)
└── README.md                  # Documentação principal do projeto

```

---

## ⚙️ Engenharia de Dados & Modelagem Dimensional

Os dados originais do IMDb possuem alta cardinalidade e volume de larga escala. O pipeline foi projetado aplicando os princípios clássicos de modelagem de Data Warehousing (Kimball):

* **Segregação de Escopo:** Filtragem e junção das chaves (`tconst`, `nconst`) para delimitar o conjunto de dados analítico.
* **Estruturação de Tabelas Fato:** Desenvolvimento da tabela `tb_fatos_filmes_brasileiros.csv`, centralizando os fatos numéricos mensuráveis (médias de avaliação e contagem de votos acumulados) associados aos eixos dimensionais (tempo e títulos).

---

## 📊 Dashboard e Insights Analíticos

O painel no Power BI foi projetado respeitando a identidade visual clássica do IMDb (tons escuros com realces em dourado), priorizando a clareza e a hierarquia de informações.

### KPIs Consolidados:

* **Filmes Totais:** **66 Mil** títulos mapeados e qualificados dentro do escopo.
* **Média de Avaliação:** **61** (em uma escala de 0 a 100), indicando uma distribuição de notas equilibrada na base analisada.
* **Votos Totais:** **71 Mil** de interações contabilizadas, garantindo relevância estatística aos dados de preferência do público.

### Análises Principais:


* **Quantidade de Filmes Avaliados por Período: A análise histórica demonstra o crescimento da produção e do engajamento crítico ao longo do tempo. O período de 2001-2026 concentra o maior volume, registrando 29.937 títulos avaliados, em contraste com apenas 209 títulos entre 1895-1920.

* **Filmes que Mais Receberam Votos: O ranking destaca o domínio de grandes franquias e clássicos, liderados por Star Wars: Episode IV (47 Mi de votos), seguido por Star Wars: Episode V (45 Mi), Star Wars: Episode VI (36 Mi), além de sucessos como The Shawshank Redemption, The Avengers e The Dark Knight.

