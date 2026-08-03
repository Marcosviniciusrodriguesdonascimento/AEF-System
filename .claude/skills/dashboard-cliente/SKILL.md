---
name: dashboard-cliente
description: Construção ou atualização de dashboard Power BI para um cliente — do levantamento de requisitos à validação dos números e entrega. Use quando o usuário pedir para criar, revisar ou atualizar um dashboard/painel de um cliente.
---

# Dashboard Power BI para Cliente

Fluxo de construção de dashboard com números confiáveis — o erro que destrói a credibilidade de um dashboard é o número errado, não o visual feio.

## Etapas

### 1. Requisitos (`gestor-projetos`)
- Quem vai usar, quais decisões o painel apoia, com qual frequência de atualização.
- Liste os KPIs com **definição escrita de cada um** (fórmula, fonte, período) — aprovada pelo cliente antes de construir.

### 2. Preparação dos dados (`analista-dados`)
- Tratamento das fontes, granularidade correta, tabela calendário, reconciliação com os relatórios oficiais do cliente.

### 3. Modelagem e medidas (`especialista-powerbi`)
- Modelo estrela, relacionamentos documentados, medidas DAX explícitas e comentadas — uma medida por KPI aprovado, sem cálculos duplicados.

### 4. Layout (`especialista-powerbi`)
- Hierarquia visual: KPIs principais no topo → tendência → detalhamento. Página inicial responde as 3 perguntas mais importantes do cliente sem cliques.
- Antes de desenhar qualquer visual, consulte a skill `dataviz` para escolhas de gráfico e cor.

### 5. Validação de números (`revisor-financeiro`) — obrigatória
- Cada KPI do dashboard conferido contra a fonte (DRE, extrato, relatório contábil) para o mesmo período.
- Divergência encontrada = corrigir antes de mostrar ao cliente, sem exceção.

### 6. Entrega e treinamento (`redator-executivo` + `gestor-projetos`)
- Reunião de entrega mostrando como ler o painel; documento de 1 página com a definição de cada KPI; combinar rotina de atualização.

## Regras
- Nenhum dashboard vai ao cliente sem a etapa 5 concluída.
- Definição de KPI aprovada por escrito é o contrato do dashboard — mudanças depois são changes de escopo (registrar via `gestor-projetos`).
- Dashboard e relatório mensal do mesmo cliente devem sempre bater — mesma fonte, mesmas definições.
