# Analytics de Performance de Vendas (Oracle SQL)

Este projeto consiste em uma **query analítica robusta (SQL)** desenvolvida para extrair, transformar e consolidar indicadores de performance comercial (KPIs) diretamente do ERP Winthor (Oracle Database).

O objetivo é fornecer uma visão 360º da performance do vendedor, indo além do simples "Vendido vs. Meta", integrando dados de CRM, logística e financeiro.

## 🎯 Problema de Negócio Resolvido
Relatórios padrões de ERPs muitas vezes entregam dados fragmentados. Para uma gestão estratégica, era necessário cruzar:
1. **Eficiência de Vendas:** Atingimento de meta e projeção baseada em dias úteis.
2. **Saúde da Carteira (CRM):** Identificar automaticamente clientes recuperados (Reativação) e risco de perda (Churn).
3. **Qualidade da Venda:** Monitorar a margem de contribuição e a inadimplência gerada pelo vendedor.

## 🛠️ Tecnologias Utilizadas
* **Oracle SQL:** Uso intensivo de *Common Table Expressions (CTEs)* para modularidade e *Window Functions*.
* **Lógica de Negócio:** ERP Winthor (Tabelas PCPEDC, PCPEDI, PCCLIENT, PCUSUARI, etc).

## 📊 Principais KPIs Calculados
A query gera uma matriz com os seguintes indicadores por RCA (Representante Comercial):

| Indicador | Descrição | Regra de Negócio |
| :--- | :--- | :--- |
| **Projeção de Vendas** | Estimativa de fechamento | `(Venda Atual / Dias Úteis Passados) * Dias Úteis Totais` |
| **Reativação** | Clientes recuperados | Clientes inativos (>90 dias) que compraram > R$ 150,00 no mês. |
| **Margem de Lucro** | Rentabilidade da venda | `(Venda Líquida - CMV - Custos Extras) / Venda Líquida` |
| **Cobertura** | Penetração na carteira | Contagem distinta de CNPJs positivados no período. |
| **Inadimplência** | Risco financeiro | Títulos vencidos há mais de 5 dias na carteira do vendedor. |

## 🚀 Como executar
A query está estruturada em blocos `WITH` (CTEs) para facilitar a leitura e manutenção.
1. Abra o arquivo `query_performance_vendedores.sql`.
2. Ajuste o parâmetro de data na CTE `PERIODO_ANALISE` (linhas 20-30).
3. Execute em ambiente Oracle Database conectado às tabelas padrões do Winthor.

---
**Autor:** [Renan Gonçalves Azanha](https://www.linkedin.com/in/renan-gon%C3%A7alves-azanha-852b5011a/)
*Focado em transformar dados complexos em decisões estratégicas.*
