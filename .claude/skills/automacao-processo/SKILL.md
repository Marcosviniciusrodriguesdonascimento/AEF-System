---
name: automacao-processo
description: Automação de um processo corporativo repetitivo — do mapeamento do processo manual ao script/pipeline em produção com validação. Use quando o usuário quiser automatizar uma rotina (coleta de dados, geração de relatório, integração entre sistemas, tratamento de planilhas).
---

# Automação de Processo Corporativo

Fluxo para automatizar com segurança — em processo financeiro, uma automação errada e silenciosa custa mais caro que o processo manual.

## Etapas

### 1. Mapeamento do processo atual (`gestor-projetos` + `engenheiro-automacao`)
- Documente o passo a passo manual: entradas (de onde vêm), transformações (o que é feito), saídas (para onde vai), frequência e tempo gasto.
- Identifique as exceções: o que acontece quando o dado vem errado/atrasado/incompleto hoje?

### 2. Desenho da solução (`engenheiro-automacao`)
- Escolha a ferramenta mais simples que resolve: fórmula/Power Query (`especialista-excel`) → script Python → integração de API. Não comece pelo mais sofisticado.
- Defina o comportamento em erro: a automação **para e avisa**, nunca continua com dado suspeito.

### 3. Implementação (`engenheiro-automacao`)
- Código com validação de entrada, logging e docstring explicando o que faz, dependências e como rodar.
- Sem credenciais no código — variáveis de ambiente ou configuração fora do git.

### 4. Teste paralelo — obrigatório
- Rode a automação em paralelo com o processo manual por pelo menos 1-2 ciclos, comparando resultados (`revisor-financeiro` confere se envolver números financeiros).
- Só desligue o processo manual depois de ciclos idênticos comprovados.

### 5. Documentação e rotina (`gestor-projetos`)
- Documento curto: o que a automação faz, quando roda, como saber se falhou, o que fazer quando falhar, quem é o responsável.
- Agende a execução (cron/Power Automate/tarefa) e o check periódico de saúde.

## Regras
- Toda automação tem modo dry-run (executa sem efeito real) para teste.
- Ação destrutiva ou externa (sobrescrever arquivo, enviar e-mail) exige confirmação explícita na primeira execução real.
- Automação sem documentação de "o que fazer quando falhar" não está pronta para produção.
