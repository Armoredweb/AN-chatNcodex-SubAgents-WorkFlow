# Guia de uso — AN-chatNcodex-SubAgents-WorkFlow

Este é o guia prático para aplicar o [workflow canônico](WORKFLOW.md) a um repositório de software existente, incluindo **continuidade entre Codex e Google Antigravity**.

## Objetivo

O **ChatGPT realiza o planejamento técnico pesado**: lê o código, decide a arquitetura, detalha contratos e algoritmos, escreve pseudocódigo/código útil, organiza as dependências e verifica consistência.

Na plataforma selecionada, o agente principal **orquestra e implementa**. O Codex pode usar Luna High; o Antigravity pode usar Gemini Flash Medium, após verificar o modelo disponível. Há dois modos: **duas capacidades** (principal barato, trabalhadores paralelos e especialista forte opcional) e **modelo único** (principal e subagentes paralelos no mesmo modelo, sem especialista forte obrigatório).

A meta é concluir rapidamente **GOALs ou lotes de GOALs independentes já autorizados**, usando mais implementação paralela quando vantajosa, e permitir que o usuário **troque de plataforma no meio da implementação**, continuando do estado salvo, sem copiar histórico. O agente principal deve priorizar coordenação e integração quando houver trabalho independente suficiente, mas pode implementar diretamente tarefas críticas.

## 1. Identifique os repositórios

- **Manual do workflow:** https://github.com/Armoredweb/AN-chatNcodex-SubAgents-WorkFlow/blob/main/docs/WORKFLOW.md
- **Repositório consumidor:** o projeto de software em que o código e os planos vivem, normalmente com a pasta `plans/<nome-do-plano>/`.
- **Workflow anterior:** referência histórica apenas; não reutilize regras de troca manual de modelo.

O repositório deste workflow armazena as instruções. Ele não recebe os planos de todos os projetos consumidores.

## 2. Configure o planejamento no ChatGPT

Crie um ChatGPT Project para o **projeto consumidor** e informe o repositório, a branch e o manual canônico. Um bloco inicial de instruções é:

~~~text
Você é a camada de planejamento ChatGPT deste repositório:
<OWNER/REPOSITORY> (branch: <BRANCH>).

Leia sempre a versão atual do workflow canônico:
https://github.com/Armoredweb/AN-chatNcodex-SubAgents-WorkFlow/blob/main/docs/WORKFLOW.md

ChatGPT é responsável por arquitetura, inspeção de código, pesquisa,
decomposição, Plan Parts, auditorias, perfis por plataforma e
convergência. Codex ou Antigravity implementa GOALs aprovados
usando IMPLEMENTATION_HANDOFF.md e delega apenas quando compensar.

Exija Minimal Context Delegation; não use ACTIVE_MODEL manual.
Dê prioridade ao repositório atual e à arquitetura aprovada, nunca à
memória da conversa. Não grave planos sem aprovação explícita.
Respeite as permissões e comunique-se comigo em pt-BR;
escreva planos técnicos preferencialmente em inglês.
~~~

Substitua os valores entre sinais de menor/maior pelo repositório e branch reais.

Primeiro comando sugerido:

~~~text
Leia o workflow canônico atual, verifique meu repositório,
branch, HEAD e arquitetura existente. Vamos fazer brainstorming
primeiro. Não crie planos nem implemente código ainda.
~~~

## 3. Aprove o planejamento

Discuta requisitos e opções. O ChatGPT deve produzir uma proposta de arquitetura e `MASTER_PLAN.md` compacto antes de expandir Plan Parts.

Ao aprovar a fase de planejamento, use algo como:

~~~text
Aprovo a arquitetura do MASTER_PLAN e autorizo o planejamento de
implementação somente dentro de plans/<nome-do-plano>/.
Prossiga com a decomposição conforme o workflow canônico.
~~~

Após a primeira decomposição e criação do índice, ocorre uma pausa obrigatória para revisão do escopo. O comando `continue` inicia o **Decomposition Audit Gate**, verificando MASTER_PLAN ↔ PLAN_INDEX nos dois sentidos.

A expansão deve priorizar **o máximo de código de implementação correto e útil que o ChatGPT conseguir produzir**, incluindo funções, interfaces, tratamento de erros, integração e pseudocódigo detalhado. O índice deve separar **dependências reais de GOALs que podem executar simultaneamente** e prever delegação proativa de análise visual, riscos altos e fragmentos muito complexos. Plan Parts maiores e ricos em código são desejáveis quando economizam raciocínio da Luna. Não reduzir código útil para deixar os planos pequenos. Planejar **somente os testes relacionados ao código alterado e às dependências/consumidores afetados**, com seletores específicos por lote/GOAL. A suíte pode crescer no repositório, mas nunca deve ser executada inteira durante a implementação.

Antes do handoff portátil de implementação, o ChatGPT executa:
- **Pass A:** otimização sem perder informações necessárias;
- **Pass B:** redução de chamadas a especialistas e análise do paralelismo;
- **Pass C:** consistência entre arquitetura, índice, Plan Parts, subagentes e código real.

## 4. Escolha a plataforma e configure os agentes

O planejamento cria `IMPLEMENTATION_HANDOFF.md` como **contrato e checkpoint portátil**. O PLAN_INDEX mantém a matriz de capacidades por plataforma, modelos exatos quando a interface permite, esforço, funções, paralelismo e limitações verificadas. Você escolhe **Codex ou Antigravity** e o modo **duas capacidades** ou **modelo único**.

No **Codex**, Luna High pode configurar `.codex/config.toml` e os agentes necessários em `.codex/agents/*.toml`.

No **Antigravity**, selecione no cliente um Gemini Flash Medium disponível ou outro modelo verificado. Os subagentes personalizados ficam em `.agents/agents/*.md`, com YAML frontmatter. O campo documentado `model: flash | pro | inherit` escolhe uma categoria, não necessariamente uma versão fixa. O `AGENTS.md` pode ser compartilhado. Não criar novos mecanismos na pasta legada `.agents/workflows/`; skills reutilizáveis são opcionais.

Execute apenas o bootstrap primeiro:

~~~text
Leia plans/<nome-do-plano>/IMPLEMENTATION_HANDOFF.md e PLAN_INDEX.md.
Execute somente Agent Bootstrap e Compatibility Gate da plataforma
e do perfil selecionados. Verifique HEAD, alterações locais,
modelos efetivos, permissões e subagentes. Preserve arquivos
existentes e configurações da outra plataforma.
Registre limitações e eventual necessidade de nova sessão.
Não inicie o GOAL ainda.
~~~

Não confunda TOML/YAML válido com confirmação de que o modelo correto foi utilizado. Alternativas só podem ser usadas quando aprovadas e verificadas.

## 5. Execute o GOAL

Depois de validar o ambiente:

~~~text
Inicie o GOAL G01 (ou o lote de GOALs expressamente autorizado)
do IMPLEMENTATION_HANDOFF.md atual.
Use o agente principal verificado da plataforma/perfil selecionados.
Verifique o que está pronto e independente; distribua implementações
simples e paralelas a dois ou mais agentes econômicos quando compensar.
Coordene as integrações e implemente diretamente o caminho crítico.
No modo de duas capacidades, delegue cedo a um especialista verificado
a análise real de imagens/capturas de tela, riscos altos ou partes
muito complexas, com referências exatas e contexto mínimo.
Não inicie GOALs não autorizados nem altere a arquitetura aprovada.
Execute apenas testes específicos do código alterado e das
dependências/consumidores afetados, usando filtros explícitos.
NUNCA execute toda a suíte durante a implementação, nem no fim
de um GOAL. Reaproveite resultados aprovados ainda válidos.
Se falhar, corrija e repita só os testes invalidados.
Não use comandos sem filtro que disparem a suíte inteira.
Comprove Expected Evidence no estado final pertinente.
Respeite arquitetura e arquivos autorizados.
Não solicite trocas manuais de modelo durante o GOAL.
~~~

O agente principal coordena e integra **GOALs autorizados e componentes independentes simultâneos**, preferencialmente delegando implementação simples a trabalhadores econômicos quando houver ganho. Ele também pode implementar diretamente o trabalho crítico. Falhas normais são corrigidas sem escalonamento automático. Testes antecipados ficam reservados a contratos fundamentais ou riscos altos. Testes anteriormente aprovados só devem ser repetidos quando o código coberto, suas dependências relevantes, seus seletores ou o ambiente/configuração mudarem; após uma correção, executar apenas os testes impactados. A suíte completa continua crescendo como conjunto de testes disponíveis, mas nunca é executada automaticamente durante um GOAL. No modo de duas capacidades, deve considerar um especialista mais capaz **proativamente** para avaliar imagens/capturas reais, composição visual, tarefas de alto risco ou muito complexas; preferir **Visual Review / Solve Only** e usar **Scoped Implementation** quando necessário. Enviar apenas os arquivos, referências de imagem e contratos mínimos, sem fazer o especialista procurar todo o projeto. No modo de modelo único não deve chamar um modelo mais caro sem nova autorização.

O especialista pode solicitar arquivos adicionais específicos e justificar a necessidade; Luna só autoriza ampliação operacional dentro dos limites já aprovados.

Pausas podem ocorrer por permissões, limitações da plataforma, nova sessão necessária ou decisão arquitetural genuína. Retomar uma sessão pausada não é o mesmo que trocar manualmente de modelo.

## 6. Troca de plataforma, validação e encerramento

Se uma plataforma atingir seu limite ou você preferir outra, a execução deve preservar um checkpoint pequeno em `IMPLEMENTATION_HANDOFF.md`: **GOALs autorizados ativos/concluídos/bloqueados**, partes integradas e pendentes por GOAL, HEAD/alterações locais, testes ainda válidos, **responsáveis por worktrees e imagens/capturas acessíveis**, integrações e subagentes pendentes, bloqueios e próximos passos exatos. É necessário interromper trabalhos concorrentes ou registrar explicitamente os que não foram integrados.

Na nova plataforma, abra o mesmo projeto/repositório e use:

~~~text
Continue o GOAL aprovado a partir de
plans/<nome-do-plano>/IMPLEMENTATION_HANDOFF.md.
Verifique HEAD, alterações locais, responsáveis por escritas,
partes concluídas, pendências e testes ainda válidos.
Valide o perfil de agentes desta plataforma e distribua
em paralelo o que estiver pronto e independente dentro dos
GOALs já autorizados. Se houver análise visual/de alto risco,
roteie para especialista capaz e verificado, quando permitido.
Implemente somente os passos restantes, sem repetir o histórico.
~~~

Ao retomar, execute somente os seletores de testes afetados ou invalidados, jamais toda a suíte como ritual de recuperação. Se o limite interromper a sessão abruptamente, o último checkpoint pode estar incompleto; o novo agente compara o arquivo com o código real antes de continuar. Alterações sem commit **não viajam entre computadores** por causa de um handoff: é preciso o mesmo diretório, commit ou patch explícito. A troca depende da sua ação e respeita os limites e permissões de cada serviço.

### Validação final

Ao concluir um GOAL, o agente principal apresenta evidências objetivas: arquivos alterados, integrações, **testes específicos executados e seus resultados**, Expected Evidence, chamadas a subagentes e limitações. Números de tokens e modelo realmente utilizado só devem ser relatados quando houver dados confiáveis.

O ChatGPT faz o **Convergence Check**, comparando código real e requisitos aprovados e reaproveitando evidências válidas. A suíte completa poderá ser executada **somente em uma etapa separada de validação final do sistema/release, quando solicitada ou exigida**, nunca automaticamente durante GOALs. Após convergência, prepara o `CLEANUP_HANDOFF.md` portátil. A limpeza exige **novo início explícito** do usuário, na plataforma compatível escolhida; não é automática.

## 7. Continuidade e segurança

Em um novo chat, leia o manual e os arquivos atuais necessários (`PROJECT.md`, `CHAT_HANDOFF.md`, `MASTER_PLAN.md`, `PLAN_INDEX.md` e apenas Plan Parts relevantes). Nunca trate a memória como fonte de verdade.

**Manual Mode:** uma operação substancial coerente por comando. **Continuous Mode:** execução opt-in com checkpoints e verificação de segurança do contexto. `CHAT_HANDOFF.md` pertence à continuidade entre chats do planejamento; `IMPLEMENTATION_HANDOFF.md` pertence à continuidade real da implementação entre plataformas.

A delegação com contexto mínimo **não é sandbox de arquivos**. Permissões reais, worktrees e outras medidas técnicas podem ser necessárias. Respeite limites de uso, segurança e autorização.

## Licença

[Creative Commons Attribution 4.0 International (CC BY 4.0)](../LICENSE). Detalhes operacionais e fontes oficiais permanecem em [WORKFLOW.md](WORKFLOW.md).
