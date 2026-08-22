# Dashboard de Análise de Vendas — Looker Studio

Dashboard interativo desenvolvido no Google Looker Studio (Data Studio) para análise de vendas de uma empresa fictícia, cobrindo o período de **dezembro/2024 a junho/2025**.

🔗 **Link do dashboard:** https://datastudio.google.com/s/vuSLqQ4XNXQ

---

## 📊 Sobre os dados

A base de dados (`dados_vendas_empresa_completo.xlsx`) contém os seguintes campos:

| Campo | Descrição |
|---|---|
| Data da Venda | Data em que a venda ocorreu |
| ID do Cliente / Nome do Cliente | Identificação do comprador |
| Estado | UF onde a venda foi registrada |
| Categoria | Categoria do produto (Alimentos, Vestuário, Brinquedos, Eletrônicos, Móveis) |
| Produto | Produto específico vendido |
| Quantidade | Unidades vendidas |
| Preço Unitário | Valor unitário do produto |
| Total Vendas | Quantidade × Preço Unitário |

> **Observação:** os dados de junho/2025 são parciais, pois o mês estava em andamento no momento da coleta (isso é sinalizado visualmente em todos os gráficos que envolvem a dimensão de tempo).

---

## 📈 Gráficos construídos

### 1. Vendas Mensais (dez/2024 – jun/2025)
Gráfico de barras mostrando o total de vendas por mês.
- Fevereiro/2025 se destaca como o mês de maior faturamento (R$ 315,8 mil).
- Aviso textual de "dados parciais" sobre a barra de junho, para não passar a falsa impressão de queda real nas vendas.

### 2. Quantidade Vendida por Mês
Gráfico de linha equivalente ao anterior, mas usando a métrica Quantidade em vez de valor monetário.
- Pico em janeiro/2025, com 196 unidades vendidas.

### 3. Vendas por Categoria
Gráfico de barras horizontais comparando as 5 categorias de produto.
- Categoria líder: **Alimentos** (R$ 378,8 mil).
- Valores das categorias são próximos entre si (378,8 mil a 286,9 mil), por isso um gráfico de pizza foi descartado (ver seção de decisões abaixo).

### 4. Top 10 Produtos Mais Vendidos
Gráfico de barras horizontais com os 10 produtos de maior faturamento.
- Produto líder: **Jogo de Tabuleiro** (R$ 123,9 mil).
- Métrica "Quantidade" incluída como métrica opcional (visível ao passar o mouse), complementando o valor de vendas.

### 5. Top 7 Estados em Vendas
Gráfico de barras horizontais com os estados de maior faturamento.
- Estado líder: **Bahia** (R$ 393,9 mil).

### 6. Cartões-resumo (Scorecards)
Total Vendas, Média de Total Vendas e Contagem de Vendas do período selecionado, com comparação percentual e um controle de período (date range) para filtrar o dashboard interativamente.

---

## 🖱️ Interatividade

- **Cruzamento de filtros (cross-filtering):** ativado nos gráficos da mesma página, ao clicar em uma barra, os demais gráficos da página se filtram automaticamente.
- **Limitação identificada:** o cruzamento de filtros por clique funciona apenas dentro da mesma página. Para sincronizar filtros entre páginas diferentes, é necessário usar um **controle de dimensão** (dropdown) com escopo definido para "todas as páginas".
- **Controle de período:** permite à equipe restringir a análise a um intervalo de datas específico; configurado como "Período automático" para não travar a visualização padrão em um intervalo fixo.

---

## 🧠 Decisões de design e lições aprendidas

1. **Ordem cronológica é obrigatória em séries temporais.** O erro mais recorrente no processo foi o Looker Studio ordenar o eixo X por valor (do maior para o menor) em vez de por data, o que distorce completamente a leitura de um gráfico de tendência. Esse é o primeiro item a conferir em qualquer gráfico de linha ou barra temporal.

2. **Gráfico de pizza não é adequado quando as fatias têm valores próximos.** No caso das categorias de produto (378,8 mil vs. 363,7 mil vs. 331 mil...), a pizza dificultava a comparação visual. Trocado por um gráfico de barras horizontais ordenado, que comunica as diferenças com muito mais precisão.

3. **Gráficos de dispersão (bolha) não permitem rótulos de texto personalizados.** Ao tentar mostrar "produto + quantidade" fixo sobre cada ponto, descobrimos que esse tipo de gráfico só permite mostrar a dimensão (nome) como rótulo, não uma combinação com a métrica. Para esse caso, um gráfico de barras horizontal com "métricas opcionais" foi a alternativa mais confiável.

4. **Formatação condicional fixa (destacar um "líder") pode conflitar com o destaque dinâmico do cross-filtering.** Se um gráfico tem uma regra fixa colorindo sempre o mesmo item (ex: Bahia sempre laranja) e ao mesmo tempo usa a cor de seleção dinâmica do clique, as duas cores se sobrepõem e confundem qual item está realmente selecionado. É preciso escolher um dos dois comportamentos.

5. **Títulos com valores embutidos ficam desatualizados quando filtros são aplicados.** Um título como "Alimentos Lidera as Vendas com R$ 378,8 mil" é ótimo na visão padrão (sem filtro), mas ao aplicar filtros interativos o valor exibido nas barras muda e o texto do título não acompanha automaticamente é uma limitação a se ter em mente ao usar esse padrão de título.

---

## ✅ Conclusões gerais

- **Bahia** é o estado com maior faturamento acumulado no período analisado.
- **Alimentos** é a categoria de produto mais vendida em valor.
- **Jogo de Tabuleiro** é o produto individual de maior faturamento.
- **Fevereiro/2025** foi o mês de pico de vendas em valor monetário; **janeiro/2025** foi o mês de pico em quantidade de unidades vendidas, mostrando que valor e volume nem sempre seguem exatamente o mesmo padrão mês a mês.
- Os dados de junho/2025 devem sempre ser interpretados com a ressalva de que o mês está incompleto.
