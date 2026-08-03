# Subagentes do AEF-System

Subagentes especializados (rodam em contexto próprio, isolado e podem ser executados em paralelo) cobrindo o trabalho da consultoria — análise econômico-financeira, Power BI, automações — e as áreas adjacentes da gestão empresarial.

## Núcleo financeiro

| Agente | Papel |
|---|---|
| `analista-financeiro` | Diagnóstico financeiro: DRE, Balanço, DFC, indicadores, ROIC, EVA, valuation. |
| `coletor-dados-financeiros` | Coleta e valida dados financeiros reais em JSON padronizado, sem fallback. |
| `pesquisador-mercado` | Contexto de mercado, setor, comparáveis e macroeconomia. |
| `revisor-financeiro` | Revisão adversarial de números, fórmulas e consistência antes da entrega. |
| `contador-fiscal` | Contabilidade e tributação BR: regimes, obrigações, CPC, simulações tributárias. |
| `controller-orcamentario` | Orçamento, forecast, real vs orçado, custos, margem, precificação. |

## Dados e tecnologia

| Agente | Papel |
|---|---|
| `especialista-powerbi` | Modelagem estrela, DAX, Power Query e performance de dashboards. |
| `analista-dados` | Python/pandas, SQL, ETL, qualidade de dados e preparação de bases para BI. |
| `especialista-excel` | Fórmulas avançadas, Power Query no Excel, VBA, auditoria de planilhas, modelos. |
| `engenheiro-automacao` | Scripts, pipelines ETL e integrações para automações corporativas confiáveis. |

## Gestão e negócio

| Agente | Papel |
|---|---|
| `estrategista-empresarial` | Planejamento estratégico, OKRs, modelo de negócio, expansão e governança. |
| `gestor-projetos` | Escopo, cronograma, entregáveis por cliente, status reports e mudanças de escopo. |
| `comercial-marketing` | Propostas comerciais, precificação de serviços, prospecção e conteúdo. |
| `juridico-empresarial` | Contratos, cláusulas de risco, LGPD, societário básico (apoio, não advocacia). |
| `rh-departamento-pessoal` | Custo de pessoal, CLT×PJ, rotinas de DP, cargos e gestão de pessoas. |
| `redator-executivo` | Relatórios executivos, memos e material para board a partir das análises. |
| `assistente-executivo` | E-mails, agenda, atas, organização de arquivos e follow-ups (usa Gmail/Calendar/Drive quando conectados). |

## Skills de projeto (fluxos em `.claude/skills/`)

Fluxos reutilizáveis que orquestram os agentes acima — invocáveis por nome:

| Skill | Fluxo |
|---|---|
| `analise-completa` | Coleta → contexto → diagnóstico → revisão → relatório executivo. |
| `relatorio-mensal` | Fechamento gerencial mensal: consolidação → apuração → desvios → relatório. |
| `novo-cliente` | Onboarding: contrato → escopo → documentos → diagnóstico inicial → kickoff. |
| `proposta-comercial` | Dor do prospect → oferta → precificação validada → documento → follow-up. |
| `dashboard-cliente` | Requisitos/KPIs → dados → modelo/DAX → layout → validação → entrega. |
| `automacao-processo` | Mapeamento → desenho → implementação → teste paralelo → produção. |

## Fluxo típico de uma análise completa

```
coletor-dados-financeiros  →  analista-financeiro  →  revisor-financeiro  →  redator-executivo
                 ↑                      ↑
       pesquisador-mercado ─────────────┘
```

Os demais agentes entram sob demanda: `controller-orcamentario` e `contador-fiscal` na visão gerencial/tributária, `especialista-powerbi`/`analista-dados`/`especialista-excel` na camada de dados e dashboards, e o bloco de gestão (`estrategista-empresarial`, `gestor-projetos`, `comercial-marketing`, `juridico-empresarial`, `rh-departamento-pessoal`, `assistente-executivo`) na operação da consultoria.

## Convenção

Cada agente é um arquivo Markdown com frontmatter (`name`, `description`, `tools`, `model`) seguido do system prompt; cada skill é uma pasta em `.claude/skills/<nome>/SKILL.md`. Para ajustar comportamento, edite o arquivo correspondente. As descrições foram escritas para acionamento proativo ("Use PROACTIVELY quando...").
