# RS Spatial Delivery H3

### Análise Espacial de Entregas de E-commerce com Uber H3

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow)
![H3](https://img.shields.io/badge/Uber-H3-orange)

Este projeto foi desenvolvido como um estudo prático de **Análise Espacial**, **Engenharia de Dados** e **Data Analytics**, utilizando o sistema **Uber H3** para explorar a distribuição espacial das entregas de e-commerce no estado do Rio Grande do Sul.

A partir do conjunto de dados público da **Olist**, foi construído um pipeline em Python para integrar diferentes bases, calcular indicadores logísticos, agregá-los em uma malha hexagonal e gerar produtos para análise geoespacial e visualização de dados.

---

# Visualizações

## Mapa 3D (Pydeck)

<img width="1567" alt="Python_3d" src="https://github.com/user-attachments/assets/e8d8aba9-6f58-480e-833c-176cea725427"/>

## Dashboard (Power BI)

<img width="1174" alt="Power_BI" src="https://github.com/user-attachments/assets/6be899e5-b68c-48e7-8dc5-bfb924e48963"/>

---

# Objetivo

O objetivo deste projeto foi aplicar técnicas de análise espacial a um conjunto de dados público de e-commerce, explorando como a agregação geográfica pode facilitar a interpretação de indicadores logísticos.

Durante o desenvolvimento foram colocados em prática conceitos de:

* ETL e integração de múltiplas bases de dados;
* manipulação de dados com Pandas;
* indexação espacial utilizando Uber H3;
* geração de produtos cartográficos em GeoJSON;
* visualização geográfica em Pydeck;
* construção de dashboards no Power BI.

---

# O problema

Visualizar milhares de entregas apenas como pontos em um mapa dificulta a identificação de padrões espaciais, principalmente em áreas urbanas onde há grande concentração de registros.

Neste projeto, os pedidos foram agregados utilizando a grade hexagonal do **Uber H3**, permitindo representar indicadores logísticos em células de tamanho uniforme, em vez de coordenadas individuais.

Essa abordagem facilita a comparação entre diferentes regiões e reduz o efeito da concentração de pontos sobre a interpretação dos resultados.

---

# Metodologia

O processamento foi realizado em cinco etapas:

1. Leitura das bases do dataset da Olist.
2. Filtragem dos clientes localizados no Rio Grande do Sul.
3. Integração das tabelas de pedidos, clientes, itens e geolocalização.
4. Cálculo de indicadores operacionais de entrega.
5. Indexação espacial utilizando Uber H3 (Resolução 7) e agregação dos resultados por hexágono.

Para cada célula H3 foram calculados indicadores como:

* quantidade de pedidos;
* faturamento total;
* frete médio;
* tempo médio de entrega;
* percentual de entregas atrasadas.

---

# Base de dados

O projeto utiliza o **Brazilian E-Commerce Public Dataset by Olist**, disponível gratuitamente no Kaggle.

https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Foram utilizadas as seguintes tabelas:

| Tabela                      | Descrição                                          |
| --------------------------- | -------------------------------------------------- |
| `olist_orders_dataset`      | Informações dos pedidos, datas de compra e entrega |
| `olist_order_items_dataset` | Valores dos produtos e fretes                      |
| `olist_customers_dataset`   | Dados dos clientes e localização                   |
| `olist_geolocation_dataset` | Coordenadas geográficas dos CEPs                   |

---

# Pipeline

```text
Olist Dataset
      │
      ▼
Leitura das bases
      │
      ▼
Filtragem dos clientes (RS)
      │
      ▼
Integração das tabelas
      │
      ▼
Cálculo dos indicadores
      │
      ▼
Indexação espacial (Uber H3)
      │
      ├──────────────┬─────────────────────┐
      ▼              ▼                     ▼
Resumo CSV      GeoJSON H3         Visualização 3D
      │              │                     │
      └──────────────┴─────────────────────┘
                     │
                     ▼
              Dashboard Power BI
```

---

# Tecnologias utilizadas

* **Python**
* **Pandas**
* **H3-py**
* **GeoJSON**
* **Pydeck**
* **Power BI**

---

# Estrutura do repositório

```text
├── logiroute_rs_fleet_analytics.py
├── logiroute_rs_h3_summary.csv
├── h3_rs_cells.geojson
├── h3_rs_interactive_map.html
└── README.md
```

| Arquivo                           | Descrição                                               |
| --------------------------------- | ------------------------------------------------------- |
| `logiroute_rs_fleet_analytics.py` | Pipeline completo de processamento e agregação espacial |
| `logiroute_rs_h3_summary.csv`     | Indicadores agregados por célula H3                     |
| `h3_rs_cells.geojson`             | Geometria das células H3                                |
| `h3_rs_interactive_map.html`      | Visualização interativa em 3D                           |

---

# Como executar

## 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

## 2. Instale as dependências

```bash
pip install pandas h3 geojson pydeck
```

## 3. Baixe o dataset

Faça o download do conjunto de dados da Olist no Kaggle e coloque os arquivos `.csv` no mesmo diretório do script principal.

## 4. Execute o pipeline

```bash
python logiroute_rs_fleet_analytics.py
```

---

# Resultados

Ao final da execução são gerados três arquivos principais:

* `logiroute_rs_h3_summary.csv`, contendo os indicadores agregados por célula H3;
* `h3_rs_cells.geojson`, com a geometria da malha hexagonal;
* `h3_rs_interactive_map.html`, uma visualização interativa em 3D construída com Pydeck.

Esses produtos podem ser utilizados em ferramentas GIS, Power BI ou outras aplicações de análise espacial.

---

# Competências demonstradas

Este projeto reúne conhecimentos em:

* Engenharia de Dados (ETL);
* manipulação de dados com Pandas;
* análise espacial utilizando Uber H3;
* geoprocessamento em Python;
* geração de arquivos GeoJSON;
* visualização geográfica em Pydeck;
* construção de dashboards no Power BI;
* organização de projetos de Ciência de Dados para portfólio.

---

# Autor

**Guilherme Cardoso**

Analista de Dados Geoespaciais | Especialista em Geoprocessamento | Pós-graduando em Inteligência Artificial aplicada às Geotecnologias

Sugestões, melhorias e contribuições são sempre bem-vindas.
