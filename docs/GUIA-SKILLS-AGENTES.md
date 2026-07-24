# Guia de Skills e Agentes — AEF-System

Mapeamento do que usar em cada fluxo de trabalho do projeto, com foco em **facilitar o trabalho** e **economizar tokens**.

## Por que isso economiza tokens

- **Skills** carregam instruções só quando invocadas — em vez de colar prompts longos a cada conversa.
- **Agentes** (subagentes) leem arquivos e dados no contexto *deles* e devolvem só a conclusão. O contexto principal não recebe dumps de planilhas, logs ou dezenas de arquivos.
- **CLAUDE.md curto** dá o contexto do projeto uma única vez, em poucas linhas.

## Skills por fluxo de trabalho

### 1. Análise financeira (núcleo do projeto)
| Skill | Quando usar |
|---|---|
| `analise-financeira-integrada` | Análise econômico-financeira completa (indicadores, DRE, fluxo de caixa) |
| `financial-health` | Diagnóstico de saúde financeira |
| `financial-data-collector` | Coleta de dados financeiros externos |

### 2. Planilhas e dados
| Skill | Quando usar |
|---|---|
| `xlsx` | Qualquer leitura/criação/edição de Excel ou CSV — sempre que planilha for entrada ou saída |
| `excel-automation` | Automações recorrentes em Excel |

### 3. Relatórios e apresentações (Power BI / diretoria)
| Skill | Quando usar |
|---|---|
| `dataviz` | **Antes de qualquer gráfico ou dashboard** — garante visual consistente |
| `pdf-creator` / `pdf` | Relatórios em PDF |
| `docx` | Relatórios/memorandos em Word |
| `pptx` / `board-deck-builder` | Apresentações para diretoria |

### 4. Automações
| Skill | Quando usar |
|---|---|
| `loop` | Tarefas recorrentes (ex.: coletar dados a cada X minutos) |
| `loop-executor` + `loop-execution-evaluator` | Executar planos de implementação com avaliação por etapa |

### 5. Qualidade e manutenção do código
| Skill | Quando usar |
|---|---|
| `/review` ou `/code-review` | Revisar PRs e diffs |
| `simplify` | Limpar código após implementar |
| `security-review` | Antes de mergear mudanças que tocam dados sensíveis |

### 6. Configuração (grande economia de tokens)
| Skill | Quando usar |
|---|---|
| `init` | Gerar/atualizar o CLAUDE.md quando o projeto crescer |
| `fewer-permission-prompts` | Reduzir prompts de permissão repetidos |
| `update-config` | Ajustar settings.json, hooks e permissões |
| `skill-creator` | Transformar um fluxo repetitivo nosso em skill própria |
| `prompt-optimizer` | Enxugar prompts longos usados com frequência |

## Agentes

### Agentes do projeto (`.claude/agents/`)
| Agente | Modelo | Papel | Economia |
|---|---|---|---|
| `explorador` | Haiku | Buscar/entender código e arquivos (somente leitura) | Alta — Haiku é ~10x mais barato e os arquivos não entram no contexto principal |
| `analista-financeiro` | Sonnet | Rodar análises e cálculos sobre os dados | Alta — dados brutos ficam no contexto do agente |
| `revisor` | Sonnet | Revisar diffs antes de commit/PR | Média — revisão isolada do contexto principal |

### Agentes embutidos
- **`Explore`** — busca ampla no repositório; use em vez de abrir vários arquivos no chat.
- **`Plan`** — planejar implementações maiores antes de codar.
- **`general-purpose`** — tarefas multi-etapa autônomas.

## Regras práticas de economia de tokens

1. **Nunca cole planilhas ou logs inteiros no chat** — aponte o caminho do arquivo e deixe o agente/skill ler.
2. **Delegue buscas amplas** ao `explorador` ou `Explore`; peça só a conclusão.
3. **Um fluxo repetido 3+ vezes vira skill** (`skill-creator`) — instruções pagas uma vez, não a cada conversa.
4. **Sessões longas custam caro**: encerre e abra nova sessão quando mudar de assunto.
5. **Modelo certo para a tarefa**: Haiku para mecânico, Sonnet para análise, Opus/Fable só para o que é realmente difícil.
