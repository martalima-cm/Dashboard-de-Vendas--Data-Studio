# 📊 Dados de Vendas - Empresa (Análise Comercial & Desempenho)

Este repositório contém a base de dados consolidada e as análises de desempenho comercial, comportamento do cliente, sazonalidade de vendas e rentabilidade por linha de produto.

---

## 📌 Visão Geral do Projeto

O objetivo principal deste projeto é centralizar e estruturar as transações de vendas da empresa para apoiar a tomada de decisões estratégicas de negócios. A partir dos dados consolidados, foram desenvolvidas análises para responder a perguntas-chave sobre:

- **Performance de Produtos:** Identificação de campeões de vendas em faturamento e volume.
- **Sazonalidade:** Avaliação de picos e quedas de vendas ao longo dos meses e impacto de datas comemorativas (como Natal, Black Friday e feriados).
- **Perfil de Clientes:** Análise do Ticket Médio, comportamento de compra por região e identificação de clientes *High Value*.
- **Rentabilidade:** Cálculo e projeção das margens de lucro operacionais e custos associados por transação.

---

## 📁 Estrutura da Base de Dados

O arquivo principal do projeto é o `dados_vendas_empresa_completo.xlsx`, que está organizado nas seguintes abas (planilhas):

| Aba / Planilha | Descrição |
| :--- | :--- |
| **`dados_vendas_empresa`** | Registro bruto (*raw data*) contendo as transações detalhadas com informações do cliente, localização, categoria e valores. |
| **`Cópia_dados_vendas`** | Base processada contendo dados enriquecidos com cálculos de **Lucro estimado (40%)**, **Gastos operacionais (10%)** e segmentação temporal (**Ano** e **Mês**). |
| **`Produtos`** | Painel analítico de desempenho por linha de produtos e categorias (faturamento total vs. volume de itens vendidos). |
| **`Sazonalidade`** | Mapeamento temporal de vendas, identificando o melhor e pior mês, além da performance em datas festivas. |
| **`Cliente e Comportamento`** | Análise demográfica e comportamental da carteira de clientes ativos e recorrência de compras. |

---

## 🗂️ Dicionário de Dados

Abaixo estão os campos presentes nos registros de transações:

| Campo | Tipo de Dado | Descrição |
| :--- | :--- | :--- |
| `Data da Venda` | `Date (YYYY-MM-DD)` | Data exata em que o pedido foi finalizado. |
| `ID do Cliente` | `Integer` | Identificador único do cliente no sistema. |
| `Nome do Cliente` | `String` | Nome completo ou razão social do cliente. |
| `Estado` | `String (UF)` | Unidade Federativa do destino da entrega (ex: SP, RS, PR, BA). |
| `Categoria` | `String` | Categoria do produto (ex: Eletrônicos, Alimentos, Vestuário, Brinquedos). |
| `Produto` | `String` | Nome/Modelo do item comercializado. |
| `Quantidade` | `Integer` | Volume de unidades vendidas na transação. |
| `Preço Unitário` | `Decimal (BRL)` | Valor unitário praticado na venda. |
| `Total Vendas` | `Decimal (BRL)` | Valor total da transação (`Quantidade` × `Preço Unitário`). |
| `Lucro 40%` | `Decimal (BRL)` | Margem bruta estimada aplicada sobre a receita total. |
| `Gastos 10%` | `Decimal (BRL)` | Custos operacionais e taxas estimadas sobre a transação. |
| `Ano` / `Mês` | `Integer` | Campos derivados para facilitar agrupamentos temporais. |

---

## 💡 Principais Perguntas de Negócio Respondidas

A estrutura foi modelada para fornecer respostas rápidas para os seguintes indicadores estratégicos:

1. **Qual é o produto campeão em faturamento e em volume?**
2. **Quais são o melhor e o pior mês em vendas ao longo do período analisado?**
3. **Como se comportaram as vendas em datas festivas e feriados estratégicos?**
4. **Quem são os principais clientes (top buyers) e qual é o seu perfil de compra?**

---

## 🛠️ Ferramentas e Tecnologias Utilizadas

- **Microsoft Excel:** Tratamento de dados, fórmulas dinâmicas e dashboards analíticos.
- **Markdown:** Documentação e padronização do repositório.

---

## ✒️ Autor

Projeto mantido por **[martalima-cm](https://github.com/martalima-cm)**.
