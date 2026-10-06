# 📊 Dashboard de Vendas – Xbox Game Pass

Dashboard em Excel que transforma a base bruta de assinaturas do Xbox Game Pass em indicadores e gráficos para apoiar decisões de vendas.

## Objetivo
Responder perguntas de negócio sobre o faturamento das assinaturas, de forma visual e com filtro interativo.

## Dados utilizados
- **Arquivo:** `data/base.xlsx` (aba *Bases*), 295 assinaturas iniciadas entre jan e dez/2024.
- **Colunas:** ID do assinante, nome, plano (Core / Standard / Ultimate), data de início, auto renovação, preço da assinatura, tipo (Monthly / Quarterly / Annual), EA Play Season Pass (sim/não e preço), Minecraft Season Pass (sim/não e preço), cupom e valor total.
- **Qualidade verificada:** sem valores nulos, sem IDs duplicados, e `Total Value = assinatura + EA Play + Minecraft − cupom` em 100% das linhas.
- **Observação:** em `EA Play Season Pass Price`, quem não contratou o item aparece com `-` (texto). As fórmulas `SUMIFS` ignoram texto, então o resultado não é afetado.

## Estrutura do arquivo `dashboard_xbox.xlsx`
| Aba | Conteúdo |
|---|---|
| **Dashboard** | KPIs, 6 gráficos e filtro por tipo de assinatura (canto superior direito, célula Q2) |
| **Cálculos** | Perguntas de negócio (PN1 a PN6) e KPIs, todos com fórmulas |
| **Bases** | Dados brutos em tabela do Excel (`Tabela1`) |

## Indicadores e gráficos
- **KPIs:** faturamento total, nº de assinantes, ticket médio, cupons concedidos, vendas de EA Play e vendas de Minecraft.
- **Gráficos:** faturamento por plano, por auto renovação, por tipo de assinatura, por mês de início, e vendas de EA Play e Minecraft por plano.

## Principais resultados (todos os tipos)
- Faturamento total: **R$ 7.633** com **295** assinantes (ticket médio **R$ 25,87**).
- O plano **Ultimate** gera **R$ 5.388 (~71%)** do faturamento.
- Auto renovação divide a base ao meio: 50,2% dos assinantes (R$ 3.786) contra R$ 3.847 sem renovação.
- Cupons concederam **R$ 2.122** em descontos.
- EA Play: R$ 2.940, só no plano Ultimate. Minecraft: R$ 3.880, em Standard e Ultimate.
- Jan e fev têm pouca receita (R$ 65 e R$ 82), e de mar a nov o faturamento mensal fica estável (R$ 770 a R$ 830). Dez é parcial (base vai até 16/12).

## Como reproduzir
1. Baixe este repositório e abra `dashboard_xbox.xlsx` no Excel (2010 ou superior).
2. Use o filtro da célula **Q2** da aba Dashboard (Todos, Monthly, Quarterly, Annual). Tudo recalcula sozinho.
3. Para usar dados novos, cole-os na aba **Bases** (mesmas colunas, dentro da `Tabela1`). As fórmulas em **Cálculos** usam o intervalo A2:M296, então ajuste-o se a quantidade de linhas mudar.
4. Do zero: importe `data/base.xlsx`, crie as fórmulas `SUMIFS` por plano, auto renovação, tipo e mês, e monte os gráficos de barras com a paleta verde (`#22C55E`) e fundo cinza (`#E8E6E9`).

## Ferramentas
Excel (fórmulas `SUMIFS`, `COUNTIFS`, validação de dados e gráficos).
