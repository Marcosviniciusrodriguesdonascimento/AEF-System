# Recursos do GitHub úteis para o AEF-System

Levantamento curado de repositórios públicos que podem ser aproveitados no
AEF-System (consultoria econômico-financeira com Claude Code, Power BI e
automações).

Critério de seleção: relevância direta para o que já existe no repositório
(17 subagentes + 6 skills de processo), preferência por projetos ativos e com
tração. Estrelas e datas conferidas em setembro/2026.

> Nada aqui foi instalado ou copiado para o repositório. É um mapa para
> decidir o que vale integrar.

---

## 1. Coleções de skills e subagentes (expandir o time de agentes)

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | 53,8k | Índice de referência de skills, agentes, status lines, hooks e plugins. Melhor ponto de partida para achar padrões de escrita de skill. |
| [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | 34,0k | 1000+ skills da comunidade, compatíveis com Claude Code. Fonte para skills de nicho que ainda não temos (revisão de contratos, QA de dados, etc.). |
| [davepoon/buildwithclaude](https://github.com/davepoon/buildwithclaude) | 3,4k | Hub com CLI própria para instalar skills/agents/commands/hooks. Útil se quisermos um fluxo de instalação em vez de copiar arquivos à mão. |
| [softaworks/agent-toolkit](https://github.com/softaworks/agent-toolkit) | 2,5k | Skills com scripts embutidos para workflows profissionais (documentação, planejamento). Bom modelo de skill "com código", que hoje não usamos. |
| [glittercowboy/taches-cc-resources](https://github.com/glittercowboy/taches-cc-resources) | 2,0k | Comandos e subagentes bem escritos; útil como referência de estilo. |
| [lst97/claude-code-sub-agents](https://github.com/lst97/claude-code-sub-agents) | 1,7k | Coleção de subagentes especializados — comparar com os nossos 17 para achar lacunas. |

**Ação sugerida:** varrer `awesome-agent-skills` e `agent-toolkit` procurando
skills de *revisão adversarial*, *QA de dados* e *geração de documentos*, que
complementam `revisor-financeiro` e `redator-executivo`.

## 2. MCP servers para o dia a dia da consultoria

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [haris-musa/excel-mcp-server](https://github.com/haris-musa/excel-mcp-server) | 4,2k | Ler e escrever `.xlsx` direto pelo agente (fórmulas, formatação, gráficos). Encaixe direto com `especialista-excel` e com o fechamento mensal. Python/openpyxl, ativo. |
| [negokaz/excel-mcp-server](https://github.com/negokaz/excel-mcp-server) | 1,0k | Alternativa em Go, foco em leitura/escrita rápida de planilhas grandes. |
| [Alex2Yang97/yahoo-finance-mcp](https://github.com/Alex2Yang97/yahoo-finance-mcp) | 350 | Expõe yfinance como MCP: cotações, demonstrações, opções, notícias. Substituiria parte do script do `coletor-dados-financeiros`. |
| [luannamorim/mcp-forge](https://github.com/luannamorim/mcp-forge) | 1 | MCP brasileiro: parsing de OFX/CSV bancário com correções por banco, categorização PT-BR, validação de CPF/CNPJ, consulta CNAE. Projeto novo e pequeno — vale como **referência de implementação**, não como dependência. |

**Ressalva sobre Power BI:** não existe hoje um MCP server de Power BI/Fabric
com maturidade (os que aparecem têm 0–2 estrelas). Para o
`especialista-powerbi`, o caminho realista continua sendo gerar DAX/M como
texto e usar a API REST do Power BI via script próprio.

## 3. Dados brasileiros (macro, mercado e regulatório)

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [wilsonfreitas/python-bcb](https://github.com/wilsonfreitas/python-bcb) | 126 | Interface Python para os web services do Banco Central: SGS (Selic, IPCA, câmbio), Expectativas de Mercado (FOCUS), moedas. Ativo (ago/2026). **É o item mais diretamente aproveitável desta seção** — alimenta o `pesquisador-mercado` com taxas macro reais. |
| [edugca/xlFOCUS](https://github.com/edugca/xlFOCUS) | 13 | Puxa FOCUS, SGS, IPEADATA, IBGE e SCR **direto para o Excel** (VBA). Útil para clientes que trabalham só em planilha. Sem atualização desde 2024. |
| [rafacmc/fibra](https://github.com/rafacmc/fibra) | 13 | Precificação de renda fixa brasileira (títulos públicos e privados). |
| [Quantilica/tesouro-direto-fetcher](https://github.com/Quantilica/tesouro-direto-fetcher) | 4 | Download de dados do Tesouro Direto — insumo para taxa livre de risco em valuation. |
| [gustavomoers/FinanceDash](https://github.com/gustavomoers/FinanceDash) | 18 | Dashboard do mercado brasileiro com dados de B3/CVM em Dash/Plotly. Referência de como coletar dados da CVM. |

## 4. Dados de mercado e análise (base internacional)

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [ranaroussi/yfinance](https://github.com/ranaroussi/yfinance) | 25,2k | Padrão de fato para dados de mercado. Já é o que o `coletor-dados-financeiros` pressupõe. |
| [defeat-beta/defeatbeta-api](https://github.com/defeat-beta/defeatbeta-api) | 746 | Alternativa ao Yahoo Finance com mais confiabilidade; inclui transcrições de earnings calls e receita por segmento/geografia. Bom plano B quando o yfinance quebra por rate limit. |

## 5. Fiscal, contábil e SPED (preenche a lacuna da rodada anterior)

Numa busca com termos mais diretos (a rodada anterior usou termos compostos
demais e voltou vazia), apareceu justamente o que faltava para o
`contador-fiscal`:

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [DeHor-Labs/mcp-fiscal-brasil](https://github.com/DeHor-Labs/mcp-fiscal-brasil) | 295 | **O achado mais relevante desta rodada.** MCP server fiscal brasileiro: CNPJ, NF-e, NFS-e, CT-e, SPED, eSocial, Simples Nacional, já com a Reforma Tributária 2026. 44 tools, tabelas offline (não depende de webservice externo instável), Python, ativo (set/2026). Encaixe direto com o `contador-fiscal` — dá a ele consulta estruturada em vez de depender só do conhecimento no prompt. |
| [robertoecf/OpenFinData](https://github.com/robertoecf/OpenFinData) | 9 | Infraestrutura de dados financeiros públicos do Brasil (API REST + MCP + CLI): BCB, CVM, ANBIMA, ANEEL, IPEA, SICONFI, SUSEP, Tesouro Direto. Pequeno e novo, mas é a primeira coisa que achamos cobrindo CVM de forma empacotada — vale acompanhar mais do que adotar já. |
| [akretion/nfelib](https://github.com/akretion/nfelib) | 207 | Bindings Python para ler/gerar XML de NF-e, NFS-e nacional, CT-e, MDF-e, BP-e. Base sólida se algum cliente precisar de emissão/leitura de nota fiscal via automação. |
| [TadaSoftware/PyNFe](https://github.com/TadaSoftware/PyNFe) | 590 | Cliente Python mais antigo e estrelado para o webservice de NF-e (SEFAZ). Referência, mas `nfelib` está mais ativo. |
| [Engenere/BrazilFiscalReport](https://github.com/Engenere/BrazilFiscalReport) | 124 | Gera os PDFs (DANFE, DACTE, DAMDFE, DACCe, DANFSe) a partir dos XMLs fiscais. Complementa `nfelib`/`PyNFe` quando o entregável final precisa ser o documento visual. |

## 6. Comunicação com cliente e automação de workflow

Áreas que a rodada anterior não cobriu: como o `assistente-executivo` fala
com o cliente fora de e-mail, e como automatizar processos sem escrever tudo
em Python puro.

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [lharries/whatsapp-mcp](https://github.com/lharries/whatsapp-mcp) | 6,2k | MCP server de WhatsApp — ler e enviar mensagens direto pelo agente. De longe o mais estrelado e ativo dos MCPs de WhatsApp que existem. Encaixe natural com `assistente-executivo` para follow-up de cliente, se o uso via WhatsApp Web for aceitável para o negócio (não é a API oficial do WhatsApp Business). |
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | 203,9k | Plataforma de automação de workflow self-hosted, com nós de IA e 400+ integrações. Não substitui os scripts do `engenheiro-automacao`, mas é uma opção viável para automações que um cliente final precisa operar/visualizar sozinho (sem depender de rodar Python). Vale considerar quando o entregável for "processo automatizado que o cliente mantém", não um script nosso. |

**Ressalva:** não achei um MCP de Google Sheets com tração real (o maior
tinha 20 estrelas) — para isso, a integração `Google_Drive`/`Google_Docs` já
disponível neste ambiente resolve a maior parte do caso de uso.

## 7. O que **ainda não** encontrei (lacunas reais)

- **Demonstrações financeiras da CVM (DFP/ITR) empacotadas como biblioteca
  Python madura**: `OpenFinData` é o candidato mais próximo, mas é recente e
  pequeno (9 estrelas) — não trataria como dependência de produção ainda.
- **MCP de Power BI maduro**: ver ressalva na seção 2 — continua sem opção
  confiável.
- **Google Sheets como MCP com tração**: ver ressalva acima; usar a
  integração Google já disponível em vez de adicionar um MCP de terceiros.

## 8. Prioridade sugerida de adoção

1. **`python-bcb`** — ganho imediato e baixo risco no `pesquisador-mercado`.
2. **`mcp-fiscal-brasil`** — maior ganho potencial desta rodada; dá ao
   `contador-fiscal` consulta estruturada de CNPJ/NF-e/SPED/eSocial em vez de
   depender só do prompt. Testar em ambiente isolado antes de expor a cliente.
3. **`excel-mcp-server` (haris-musa)** — impacto alto no `especialista-excel` e
   no `relatorio-mensal`; testar primeiro em ambiente isolado.
4. **`awesome-agent-skills`** — garimpar 2 ou 3 skills para preencher lacunas.
5. **`yahoo-finance-mcp`** — só se quisermos tirar a coleta de dados de dentro
   de script próprio.
6. **`whatsapp-mcp` (lharries)** — só depois de confirmar internamente que
   automatizar WhatsApp Web (não a API oficial) é aceitável para o negócio.
7. **`defeatbeta-api`** — deixar mapeado como fallback do yfinance.
8. **`OpenFinData`** — acompanhar sem adotar ainda; reavaliar quando o
   projeto amadurecer.

---

### Nota de método

A busca foi feita pela API de busca do GitHub a partir deste ambiente, cujo
índice é mais restrito que o site. Na primeira rodada, consultas com termos
compostos sobre nichos brasileiros (ex.: `"sped nfe nota fiscal eletronica
brasil python parser"`) voltaram vazias; nesta segunda rodada, os mesmos
temas com termos mais simples (`"nfe python"`) trouxeram resultados
relevantes. Fica o aprendizado: prefira 2–3 termos por consulta nesta API.
Ainda vale uma passada manual em [github.com/search](https://github.com/search)
para os temas que continuam sem cobertura (seção 7).
