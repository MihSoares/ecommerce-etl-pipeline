# E-commerce Data Pipeline (ETL) – Olist Dataset

## Visão Geral

Este projeto tem como objetivo construir um pipeline de dados (ETL) completo utilizando dados reais de e-commerce. A proposta é simular um ambiente de dados semelhante ao de empresas, transformando dados brutos em informações estruturadas e úteis para análise de negócio.

O pipeline realiza as etapas de extração, transformação e carga (ETL), organizando os dados em um modelo dimensional (star schema), facilitando consultas analíticas e geração de insights.

---

## Objetivo do Projeto

Responder perguntas de negócio como:

* Quais são as categorias de produtos mais vendidas?
* Qual o ticket médio dos pedidos?
* Como o tempo de entrega impacta a avaliação do cliente?
* Quais formas de pagamento são mais utilizadas?

---

## Dataset

Os dados utilizados são do **Olist E-commerce Dataset**, contendo informações reais de pedidos realizados no Brasil.

Arquivos utilizados:

* customers
* orders
* order_items
* order_payments
* order_reviews
* products
* sellers
* geolocation
* product_category_name_translation

---

## Arquitetura do Pipeline

O pipeline segue a arquitetura clássica de ETL:

1. **Extract**
   Leitura de arquivos CSV contendo dados brutos.

2. **Transform**

   * Limpeza de dados (valores nulos, tipos, duplicados)
   * Junção de múltiplas tabelas
   * Criação de métricas (valor total, tempo de entrega)
   * Padronização e enriquecimento dos dados

3. **Load**
   Armazenamento dos dados tratados em estruturas analíticas (tabelas fato e dimensão).

---

## Modelagem de Dados

O projeto utiliza **modelagem dimensional (Star Schema)**:

### Tabela Fato

**fact_sales**

* order_id
* customer_id
* product_id
* seller_id
* price
* freight_value
* total_value
* purchase_date

### Tabelas Dimensão

**dim_customers**

* customer_id
* city
* state

**dim_products**

* product_id
* category

**dim_sellers**

* seller_id
* city
* state

**dim_date**

* date
* day
* month
* year

---

## Tecnologias Utilizadas

* Python (pandas)
* SQL (SQLite/PostgreSQL)
* Jupyter Notebook
* Power BI (opcional para visualização)

---

## Estrutura do Projeto

```
ecommerce-etl-pipeline/
│
├── data/
│   ├── raw/
│   ├── processed/
│
├── src/
│   ├── extract.py
│   ├── transform.py
│   ├── load.py
│   └── main.py
│
├── sql/
│   └── schema.sql
│
├── notebooks/
│   └── analysis.ipynb
│
├── README.md
└── requirements.txt
```

---

## Principais Insights

* A maior parte das vendas está concentrada em poucas categorias de produtos
* O tempo de entrega impacta diretamente na avaliação do cliente
* Cartão de crédito é a forma de pagamento predominante
* Existe variação significativa de desempenho entre vendedores

---

## Como Executar o Projeto

1. Clone o repositório:

```
git clone https://github.com/MihSoares/ecommerce-etl-pipeline.git
```

2. Instale as dependências:

```
pip install -r requirements.txt
```

3. Execute o pipeline:

```
python src/main.py
```

---

## Próximos Passos

* Implementar automação com Airflow
* Criar pipeline incremental
* Integrar com dashboard no Power BI
* Deploy em ambiente cloud

---

## Autor

Milena Moraes Soares

Projeto desenvolvido com foco em aprendizado prático de Engenharia de Dados e análise de dados.
