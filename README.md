# 📊 Ingestão de dados via API Rest do Omie

Pipeline de dados em arquitetura Medallion construído no Microsoft Fabric, com ingestão via API, transformação em PySpark e carga em Lakehouse para consumo analítico via Power BI.

---

## 🧠 Arquitetura

O projeto segue o padrão **Medallion Architecture**, dividido em três camadas:

### 🥉 Bronze

* Ingestão de dados brutos a partir da API do Omie
* Armazenamento no Lakehouse sem transformações significativas
* Preservação do schema original para rastreabilidade

### 🥈 Silver

* Limpeza e padronização dos dados
* Tratamento de tipos e estruturas (ex: arrays, maps)
* Aplicação de regras de qualidade (ex: remoção de nulos, deduplicação)

### 🥇 Gold

* Modelagem orientada ao negócio
* Dados prontos para consumo analítico

---

## ⚙️ Stack Tecnológica

* **Microsoft Fabric**
* **PySpark**
* **Delta Lake**
* **Git** 
* **Power BI** 

---

## 🔄 Fluxo de Dados

1. **Extração**

   * Consumo de dados via API REST (Omie)
   * Paginação e controle de período

2. **Carga Bronze**

   * Escrita dos dados brutos no Lakehouse
   * Estrutura semi-estruturada preservada

3. **Transformação Silver**

   * Normalização de estruturas complexas
   * Conversão de tipos
   * Enriquecimento de dados

4. **Camada Gold**

   * Agregações e cálculos de negócio

---

## 📂 Estrutura do Projeto

```
notebooks/
├── 01_bronze/
│   ├── bronze_categorias.ipynb
│   ├── bronze_clientes.ipynb   
│   ├── bronze_contas.ipynb
│   ├── bronze_extratos.ipynb
│   └── bronze_titulos.ipynb
├── 02_silver/
│   ├── silver_categorias.ipynb
│   ├── silver_clientes.ipynb   
│   ├── silver_contas.ipynb
│   ├── silver_extratos.ipynb
│   └── silver_titulos.ipynb
├── 02_gold/
│   ├── gold_dim_categorias.ipynb
│   ├── gold_dim_clientes.ipynb   
│   ├── gold_dim_contas.ipynb
│   ├── gold_fato_extratos.ipynb
│   └── gold_fato_titulos.ipynb

config/
├── config.ipynb

.gitignore
README.md

```

---

## 🔐 Configuração

* Credenciais e parâmetros **não são versionados**
* Utilização de variáveis de ambiente / Spark configs:

```python
spark.conf.get("app_key")
```

---

## 🚀 Execução

Os notebooks são executados no Microsoft Fabric, podendo ser orquestrados via pipelines.

Execução típica:

1. Bronze (ingestão)
2. Silver (tratamento)
3. Gold (modelagem)

---

## 📈 Objetivo

Disponibilizar dados confiáveis e estruturados para análise financeira, permitindo a construção de dashboards e indicadores no Power BI.

---

## ⚠️ Observações

* Projeto voltado para fins de estudo e evolução em Engenharia de Dados
* Estrutura preparada para escalabilidade e boas práticas de versionamento

---
