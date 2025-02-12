# Sales Analysis

### Empresa

**ModaTech** (empresa fictícia)

### Setor

Varejo de Moda e E-commerce

### O dashboard atende quais áreas?

Comercial, Marketing e Planejamento Estratégico

### **Caso de Negócio**

A **ModaTech** (empresa fictícia) é uma varejista de moda que opera tanto em lojas físicas quanto no e-commerce. Para otimizar suas estratégias comerciais, ela precisa de uma plataforma que possa integrar dados de vendas e comportamento do consumidor.

A empresa busca uma visão completa do desempenho das suas operações para tomar decisões mais assertivas sobre **distribuição de produtos, segmentação de clientes e campanhas de marketing**. Para isso, disponibilizou dados de vendas, informações demográficas dos consumidores, campanhas de marketing passadas e feedbacks de clientes.

### **Problema de Negócio**

A **ModaTech** enfrenta desafios para entender:

1. **Desempenho de Vendas** → Há variações entre lojas físicas e online? Existem padrões sazonais ou regionais?
2. **Eficácia do Marketing** → Quais campanhas geraram mais impacto nas vendas? Como melhorar a segmentação de clientes?
3. **Comportamento do Consumidor** → Quem são os principais clientes? Quais produtos e promoções funcionam melhor para cada perfil?
4. **Otimização de Estoques e Distribuição** → Como alocar produtos de forma mais eficiente entre canais de venda para maximizar as receitas?

A solução será um **dashboard interativo** que responda a essas questões por meio de métricas e visualizações estratégicas.

### Principais perguntas

- **Quais são os padrões de vendas ao longo do tempo?**
- **Como as vendas variam entre lojas físicas e online?**
- **Quais regiões apresentam melhor desempenho de vendas?**
- **Qual foi o impacto das campanhas de marketing nas vendas?**
- **Quais segmentos de consumidores podem ser identificados a partir dos dados disponíveis?**
- **Quais são as preferências de compra de cada segmento de consumidor?**
- **Quais produtos ou promoções são mais eficazes para cada segmento?**
- **Quais produtos têm melhor desempenho em cada canal de venda (físico vs. online)?**
- **Como a distribuição de produtos pode ser ajustada para otimizar vendas?**
- **Quais estratégias de marketing podem ser aprimoradas para aumentar a satisfação do cliente?**

### 2. Objetivo

O objetivo é construir um dashboard para fornecer insights estratégicos para a **ModaTech** a partir da análise de dados de vendas, comportamento do consumidor e campanhas de marketing. 

### Dados

### **Dicionário de Dados**

### **Tabela `CLIENTES`** (Dimensão)

| Nome da Coluna | Descrição |
| --- | --- |
| `ID_CLIENTE` | Identificador único do cliente |
| `NOME_CLIENTE` | Nome do cliente |
| `SEXO` | Sexo do cliente (Masculino/Feminino) |
| `IDADE` | Idade do cliente |
| `UF` | Estado de residência do cliente |
| `CIDADE` | Cidade de residência do cliente |

---

### **Tabela `FILIAIS`** (Dimensão)

| Nome da Coluna | Descrição |
| --- | --- |
| `ID_FILIAL` | Identificador único da filial |
| `NOME_FILIAL` | Nome da filial |
| `CIDADE` | Cidade onde a filial está localizada |
| `UF` | Estado onde a filial está localizada |

---

### **Tabela `PRODUTOS`** (Dimensão)

| Nome da Coluna | Descrição |
| --- | --- |
| `ID_PRODUTO` | Identificador único do produto |
| `NOME_PRODUTO` | Nome do produto |
| `PRECO_TABELA` | Preço padrão do produto na tabela |

---

### **Tabela `VENDAS`** (Fato)

| Nome da Coluna | Descrição |
| --- | --- |
| `ID_VENDA` | Identificador único da venda |
| `DATA_VENDA` | Data em que a venda ocorreu |
| `ID_FILIAL` | Identificador da filial onde ocorreu a venda |
| `ID_CLIENTE` | Identificador do cliente que realizou a compra |
| `VALOR_VENDA` | Valor total da venda |

---

### **Tabela `VENDAS_PRODUTOS`** (Fato)

| Nome da Coluna | Descrição |
| --- | --- |
| `ID_VENDA` | Identificador da venda (chave estrangeira para a tabela `VENDAS`) |
| `ID_PRODUTO` | Identificador do produto vendido (chave estrangeira para a tabela `PRODUTOS`) |
| `QUANTIDADE` | Quantidade de unidades vendidas do produto |
| `VALOR_UNITARIO_VENDA_PRODUTO` | Preço unitário do produto na venda |
| `VALOR_VENDA_PRODUTO` | Valor total da venda do produto (quantidade * valor unitário) |
|  |  |

### **Dicionário de Dados Segmentação RFM)**

Esse dicionário possui as variáveis obtidas da segmentação RFM feita no Google Colab:

**Tabela `VENDAS_RFM`** (Fato)

| Nome da Coluna | Descrição |
| --- | --- |
| `ID_VENDA` | Identificador único da venda |
| `DATA_VENDA` | Data em que a venda ocorreu |
| `ID_FILIAL` | Identificador da filial onde ocorreu a venda |
| `ID_CLIENTE` | Identificador do cliente que realizou a compra |
| `VALOR_VENDA` | Valor total da venda |
| `RECENCY` | Tempo desde a última compra do cliente |
| `FREQUENCIA` | Quantidade de compras feitas pelo cliente |
| `VALOR_MONETARIO` | Valor total gasto pelo cliente |
| `R_SCORE` | Score de Recência (quanto menor, mais recente a compra) |
| `F_SCORE` | Score de Frequência (quanto maior, mais compras feitas) |
| `M_SCORE` | Score de Valor Monetário (quanto maior, mais gasto pelo cliente) |
| `FM_SCORE` | Score combinado de Frequência e Valor Monetário |
| `Classe` | Segmento do cliente baseado na análise RFM (Ex: "Cliente VIP", "Novato", "Desengajado", etc.) |

### Metodologia e Ferramentas

Metodologia

A abordagem será baseada no **ciclo de análise de dados**, garantindo que o dashboard seja estruturado de forma eficiente e orientada à tomada de decisão.

**Passos:**

1. **Definição dos Objetivos** → Identificar as perguntas de negócio e KPIs essenciais.
2. **Coleta e Preparação dos Dados** → Limpeza, transformação e estruturação para análise.
3. **Exploração e Análise de Dados** → Identificação de padrões, tendências e segmentação.
4. **Construção do Dashboard** → Desenvolvimento de visualizações intuitivas e interativas.
5. **Geração de Insights e Recomendações** → Tradução dos dados em ações estratégicas.

Técnicas Utilizadas

**🛒 Segmentação de Clientes**

- Análise RFM (Recência, Frequência, Monetário) para classificar clientes conforme seu valor para o negócio.

**📈 Análise de Tendências e Séries Temporais**

- Identificação de sazonalidade nas vendas.

**🎯 Avaliação de Impacto de Campanhas**

- Comparação de vendas antes e depois das campanhas (Análise de Lift).
- Testes A/B para medir a efetividade de diferentes estratégias de marketing.

Ferramentas e Tecnologias

**💻 Para Extração e Manipulação de Dados:**

- **Python (Pandas)** → Consulta, transformação, modelagem de dados e análise de dados.

**📊 Para Visualização e Dashboard:**

- **Power BI / Tableau** → Alternativas para visualização de dados e storytelling.

**Métricas e KPIs**

**📌 Desempenho de Vendas:**

- Receita total e por canal (loja física vs. online).
- Ticket médio e número de transações.
- Produtos mais vendidos e menos vendidos.
- Taxa de conversão no e-commerce.

**📌 Análise dos Produtos:**

- Número de clientes novos vs. recorrentes.
- Segmentação por faixa etária, localização e perfil de compra.
- Análise RFM (Clientes recentes, frequentes e de alto valor).

**📌 RFM:**

- 

### Links de Interesses
[Dashboard de Vendas](https://app.powerbi.com/view?r=eyJrIjoiOWI1Mzk0NTUtMmY5ZC00NjM2LWE2ZTMtMDBkYjQ3NTQyMDY5IiwidCI6IjZkMGI5OTE3LWQ4N2YtNDY2NC1hZDBkLWRjOTE4MjU4YmFjMCJ9)

### Processamento e análises

---

Para acompanhar todo processo de limpeza e segmentação dos dados, acesse o link abaixo:

https://colab.research.google.com/drive/1L_LrApTH3ai5Fo9kdxjRSrgE84Yifobu?usp=sharing

### Resultados e Conclusões

Para ler os resultados, acesse o link abaixo:

[Resultados e Conclusões](https://www.notion.so/Resultados-e-Conclus-es-18aa93e4def68177b2ceec539d5bb5b6?pvs=21)

### 💡 Recomendações
