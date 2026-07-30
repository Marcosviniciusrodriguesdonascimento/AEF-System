# Subagentes do AEF-System

Subagentes especializados (rodam em contexto próprio, isolado e podem ser executados em paralelo) para apoiar o trabalho de Análise Econômica e Financeira, Power BI e automações corporativas.

| Agente | Papel |
|---|---|
| `analista-financeiro` | Diagnóstico financeiro: DRE, Balanço, DFC, indicadores, ROIC, EVA, valuation. |
| `coletor-dados-financeiros` | Coleta e valida dados financeiros reais (mercado, demonstrações históricas) em JSON padronizado. |
| `pesquisador-mercado` | Contexto de mercado, setor, comparáveis e macroeconomia para enriquecer análises. |
| `especialista-powerbi` | Modelagem de dados, DAX, Power Query e performance de dashboards. |
| `revisor-financeiro` | Revisão adversarial de números, fórmulas e consistência antes da entrega. |
| `redator-executivo` | Transforma análise técnica em relatórios, memos e material para board. |
| `engenheiro-automacao` | Scripts, pipelines ETL e integrações para automatizar processos corporativos. |

## Como usar

Chame um agente pelo nome via a ferramenta de agentes (ex.: `Agent(subagent_type: "analista-financeiro", ...)`), ou deixe o orquestrador principal decidir com base na descrição de cada um — as descrições foram escritas para acionamento proativo (`Use PROACTIVELY quando...`).

### Fluxo típico de uma análise completa

```
coletor-dados-financeiros  →  analista-financeiro  →  revisor-financeiro  →  redator-executivo
                 ↑                      ↑
       pesquisador-mercado ─────────────┘
```

1. **coletor-dados-financeiros** busca e valida os números brutos.
2. **pesquisador-mercado** traz contexto qualitativo/macro quando necessário.
3. **analista-financeiro** produz o diagnóstico técnico.
4. **revisor-financeiro** audita o resultado antes de sair da mesa.
5. **redator-executivo** transforma tudo em relatório/deck para o destinatário final.

**especialista-powerbi** e **engenheiro-automacao** são usados sob demanda, sempre que o trabalho envolver dashboards ou automação de processos, respectivamente.

## Convenção

Cada agente é um arquivo Markdown com frontmatter (`name`, `description`, `tools`, `model`) seguido do system prompt. Para editar o comportamento de um agente, edite o arquivo correspondente — não é necessário recriar a definição.
