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

**Sobre Power BI:** a ressalva das rodadas anteriores (nenhum MCP maduro)
caiu — ver seção 7, onde aparece o MCP oficial da Microsoft.

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

**Sobre Google Sheets:** a ressalva da rodada anterior (nenhum MCP com
tração) também caiu — ver seção 7.

## 7. Power BI e Google Workspace (lacunas fechadas nesta rodada)

Buscas com termos mais diretos (`power bi mcp server`, `google sheets mcp`)
trouxeram o que as rodadas anteriores não acharam:

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [microsoft/powerbi-modeling-mcp](https://github.com/microsoft/powerbi-modeling-mcp) | 1,1k | **MCP oficial da Microsoft** para modelagem semântica do Power BI: criar/alterar tabelas, relacionamentos e medidas DAX pelo agente. Atualizado em set/2026. Muda o jogo para o `especialista-powerbi` — deixa de gerar DAX como texto e passa a operar o modelo diretamente. É o achado mais importante desta rodada. |
| [sulaiman013/powerbi-mcp](https://github.com/sulaiman013/powerbi-mcp) | 123 | Consulta em linguagem natural a datasets já publicados (roda DAX e devolve resultado). Complementa o oficial no lado da *leitura*: bom para o `analista-dados` validar números de um dashboard. |
| [jonathan-pap/powerbi-report-mcp](https://github.com/jonathan-pap/powerbi-report-mcp) | 19 | Monta o *relatório* (páginas, visuais, temas, layout) em formato PBIR. Pequeno e novo, mas é o único que cobre a camada visual. Acompanhar. |
| [d0nk3yhm/pbix-mcp](https://github.com/d0nk3yhm/pbix-mcp) | 17 | Leitura/escrita de todas as camadas de um `.pbix` (layout, DAX, M, metadados, dados VertiPaq). Útil para auditar arquivo legado de cliente sem abrir o Desktop. |
| [taylorwilsdon/google_workspace_mcp](https://github.com/taylorwilsdon/google_workspace_mcp) | 3,2k | Workspace completo (Gmail, Calendar, Docs, Sheets, Slides, Drive, Forms, Tasks) num MCP só. Se um dia quisermos sair das integrações nativas deste ambiente por uma que rode em qualquer cliente MCP, é esta. |
| [xing5/mcp-google-sheets](https://github.com/xing5/mcp-google-sheets) | 1,0k | Só Sheets, mais focado e mais leve que o anterior. Boa opção quando o caso é exclusivamente planilha compartilhada com cliente. |

**Leitura prática:** para o `especialista-powerbi`, a combinação
`powerbi-modeling-mcp` (modelo) + `powerbi-report-mcp` (visual) cobre o ciclo
inteiro do skill `dashboard-cliente`. Para Google Workspace, as integrações
nativas deste ambiente continuam suficientes; os MCPs acima valem se o fluxo
precisar rodar fora daqui.

## 8. Jurídico, RH e valuation

| Repositório | ⭐ | Por que interessa |
|---|---|---|
| [AlissonSantos1/brasil-legal-skills](https://github.com/AlissonSantos1/brasil-legal-skills) | 8 | Plugin de Claude Code (MIT) com 9 módulos e 13 calculadoras Python: IRPF, rescisão CLT, CLT vs PJ, Simples Nacional, aposentadoria INSS, Reforma Tributária com split payment. Encaixe direto com `rh-departamento-pessoal`, `contador-fiscal` e `juridico-empresarial`. Poucas estrelas, mas é o único que já vem no formato que usamos (skills + slash commands). **Conferir as fórmulas contra fonte oficial antes de usar em entregável.** |
| [neimaciel/compliance-pro-lgpd](https://github.com/neimaciel/compliance-pro-lgpd) | 0 | Skill de Claude Code para compliance LGPD: workflows, templates PT-BR (RIPD, ROPA), scanner de PII. Recém-criado, sem tração — vale como **modelo de estrutura** para uma skill própria de LGPD no `juridico-empresarial`, não como dependência. |
| [halessi/DCF](https://github.com/halessi/DCF) | 500 | Biblioteca Python de DCF: busca demonstrações e calcula valuation por parâmetros. Referência de implementação para o `analista-financeiro` — o skill `analise-completa` hoje faz valuation no prompt. |
| [stockvaluation-io/stockvaluation_io](https://github.com/stockvaluation-io/stockvaluation_io) | 32 | DCF via MCP no estilo Damodaran: ticker → premissas transparentes → cenários. Java, mas o interessante é o *desenho* (premissas auditáveis), que é o que um cliente cobra num laudo. |

**Não vale o tempo:** calculadoras avulsas de rescisão CLT (encontrei ~25, todas
com 0 estrelas e sem manutenção) e ferramentas genéricas de "revisão de
contrato com IA" (todas com 0–3 estrelas, nenhuma em português nem com base
na legislação brasileira).

## 9. O que **ainda não** encontrei (lacunas reais)

- **Demonstrações financeiras da CVM (DFP/ITR) empacotadas como biblioteca
  Python madura**: continua em aberto. `OpenFinData` (9 estrelas) segue como
  candidato mais próximo; apareceram também
  [dalmofelipe/cvmdata](https://github.com/dalmofelipe/cvmdata) (2 estrelas,
  pipeline de indicadores fundamentalistas) e alguns notebooks avulsos —
  nenhum em condição de dependência de produção.
- **Revisão de contrato com base na legislação brasileira**: nada com tração.
  Se for necessário, o caminho é skill própria no `juridico-empresarial`.

## 10. Prioridade sugerida de adoção

1. **`powerbi-modeling-mcp` (Microsoft)** — sobe para o topo: é oficial,
   ativo, e resolve a maior limitação do `especialista-powerbi`. Testar em
   um `.pbip` de exemplo antes de apontar para arquivo de cliente.
2. **`python-bcb`** — ganho imediato e baixo risco no `pesquisador-mercado`.
3. **`mcp-fiscal-brasil`** — consulta estruturada de CNPJ/NF-e/SPED/eSocial
   para o `contador-fiscal`. Testar em ambiente isolado antes de expor a
   cliente.
4. **`excel-mcp-server` (haris-musa)** — impacto alto no `especialista-excel`
   e no `relatorio-mensal`; testar primeiro em ambiente isolado.
5. **`brasil-legal-skills`** — instalar e auditar as 13 calculadoras; o que
   passar na conferência vira base para `rh-departamento-pessoal` e
   `contador-fiscal`.
6. **`awesome-agent-skills`** — garimpar 2 ou 3 skills para preencher lacunas.
7. **`powerbi-report-mcp` + `pbix-mcp`** — acompanhar; adotar quando o
   modeling-mcp já estiver em uso e a camada visual virar gargalo.
8. **`yahoo-finance-mcp`** — só se quisermos tirar a coleta de dados de dentro
   de script próprio.
9. **`whatsapp-mcp` (lharries)** — só depois de confirmar internamente que
   automatizar WhatsApp Web (não a API oficial) é aceitável para o negócio.
10. **`defeatbeta-api`** — deixar mapeado como fallback do yfinance.
11. **`OpenFinData`** — acompanhar sem adotar ainda; reavaliar quando o
    projeto amadurecer.

---

### Nota de método

A busca foi feita pela API de busca do GitHub a partir deste ambiente, cujo
índice é mais restrito que o site. Na primeira rodada, consultas com termos
compostos sobre nichos brasileiros (ex.: `"sped nfe nota fiscal eletronica
brasil python parser"`) voltaram vazias; nesta segunda rodada, os mesmos
temas com termos mais simples (`"nfe python"`) trouxeram resultados
relevantes. Fica o aprendizado: prefira 2–3 termos por consulta nesta API.

A terceira rodada confirmou a regra: `"power bi mcp server"` e `"google
sheets mcp"` acharam projetos com milhares de estrelas que as rodadas
anteriores deram como inexistentes; `"CVM demonstrações financeiras python"`
(4 termos) voltou vazio, enquanto `"cvm dados abertos"` trouxe 22 resultados.
Ainda vale uma passada manual em [github.com/search](https://github.com/search)
para os temas que continuam sem cobertura (seção 9).
