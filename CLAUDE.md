# AEF-System

Sistema de Análise Econômica e Financeira com IA, Power BI e automações corporativas.

## Stack
- Python (análises, coleta de dados, automações)
- Power BI (dashboards e relatórios)
- Excel (entrada/saída de dados financeiros)

## Convenções
- Respostas e documentação em português (pt-BR)
- Valores monetários em BRL, formato `R$ 1.234,56`
- Datas no formato `DD/MM/AAAA`

## Economia de tokens (regras para o Claude)
- Para buscas amplas no repositório, delegue ao agente `Explore` em vez de ler vários arquivos no contexto principal.
- Use os agentes de `.claude/agents/` para tarefas mecânicas (exploração, coleta, revisão) — eles retornam só a conclusão, não os dumps de arquivos.
- Leia apenas os trechos de arquivo necessários (`offset`/`limit`), nunca arquivos inteiros grandes.
- Prefira skills sob demanda (`/analise-financeira-integrada`, `xlsx`, `dataviz`) a colar instruções longas no chat.
