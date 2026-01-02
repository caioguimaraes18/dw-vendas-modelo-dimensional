# Data Warehouse – Modelo Dimensional com SQLite e Python

## 🧩 O que é um Data Warehouse (DW)

Um **Data Warehouse** é um repositório estruturado para análise de dados, voltado para apoio à decisão de negócio — diferente dos bancos transacionais usados no dia a dia operacional.

Ele organiza os dados de forma a facilitar perguntas analíticas, como:

* “Qual foi o total de vendas por produto no mês?”
* “Quais formas de pagamento são mais usadas?”

Para isso, utilizamos o modelo **Esquema Estrela**, composto por:

* **Tabela Fato** → armazena os eventos (ex.: vendas)
* **Tabelas Dimensão** → descrevem o fato (cliente, produto, tempo, pagamento etc.)

Uma analogia simples: pense em uma planilha de vendas.
As linhas são as vendas (fato) e os detalhes vêm das dimensões.

- - -

## Conceito do Projeto

Este projeto constrói um **mini Data Warehouse de Vendas** utilizando:

* Python + Pandas → transformação e modelagem dos dados
* SQLite → banco relacional leve
* Notebook Jupyter → execução e documentação do fluxo

O objetivo é demonstrar, na prática, como:

1. Ler dados brutos
2. Criar tabelas dimensão
3. Criar a tabela fato
4. Relacionar tudo no banco
5. Preparar os dados para análises de BI

- - -

## 🗂️ Modelagem Dimensional

### Dimensões criadas

* `dim_cliente`
* `dim_produto`
* `dim_pagamento`
* `dim_tempo`

Cada dimensão armazena atributos descritivos.
Exemplo em `dim_tempo`:

* dia
* mês
* ano
* dia\_da\_semana

Isso permite análises como:

* total por mês
* total por dia da semana

### Tabela Fato

* `fato_vendas`

Principais campos:

* chaves para as dimensões
* quantidade
* valor
* receita total

Cada linha representa um **evento de venda**.

- - -

## Pipeline do Projeto

1. Carrega os dados brutos com Pandas
2. Normaliza colunas e gera chaves dimensionais
3. Cria o schema no SQLite
4. Popula as dimensões
5. Popula a tabela fato
6. Relaciona tudo via chaves estrangeiras

Resultado: uma base pronta para ferramentas de BI (Power BI, Metabase etc.).

- - -

## ▶️ Como Executar

1. Instale as dependências:

```bash
pip install pandas
```
2. Abra o notebook:

```bash
main.ipynb
```
3.Execute as células na ordem

O banco será criado localmente em SQLite.

### Possíveis Evoluções

- Criar dashboard em Power BI

- Incluir novas dimensões (loja, categoria, canal)

- Implementar carga incremental

- Migrar para um DW corporativo (Postgres / BigQuery)

