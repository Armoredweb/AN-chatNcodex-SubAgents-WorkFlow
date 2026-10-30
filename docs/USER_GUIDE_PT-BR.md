# Guia de uso — AN-chatNcodex-SubAgents-WorkFlow

Este é o guia prático para aplicar o [workflow canônico](WORKFLOW.md) a um repositório de software existente.

## Objetivo

O **ChatGPT realiza o planejamento técnico pesado**: lê o código, decide a arquitetura, detalha contratos e algoritmos, escreve pseudocódigo/código útil, organiza as dependências e verifica consistência.

No Codex, **Luna High atua como orquestrador e implementador principal**. Ele implementa diretamente sempre que possível. Subagentes Luna executam tarefas independentes somente quando o paralelismo compensa; um especialista mais capaz (como SOL High) recebe apenas dificuldades justificadas e contexto mínimo.

A meta é concluir cada GOAL autonomamente **sem troca manual de modelos**.

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
decomposição, Plan Parts, auditorias, planejamento de subagentes e
convergência. Codex Luna High implementa os GOALs aprovados e delega
somente quando houver benefício comprovado.

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

A expansão deve priorizar **o máximo de código de implementação correto e útil que o ChatGPT conseguir produzir**, incluindo funções, interfaces, tratamento de erros, integração e pseudocódigo detalhado. Plan Parts maiores e ricos em código são desejáveis quando economizam raciocínio da Luna. Não reduzir código útil para deixar os planos pequenos. Planejar **poucos testes essenciais por lote/GOAL**, sem exigir teste para cada Plan Part.

Antes do handoff ao Codex, o ChatGPT executa:
- **Pass A:** otimização sem perder informações necessárias;
- **Pass B:** redução de chamadas a especialistas e análise do paralelismo;
- **Pass C:** consistência entre arquitetura, índice, Plan Parts, subagentes e código real.

## 4. Bootstrap e compatibilidade do Codex

O índice e o handoff devem registrar **IDs/versões exatos dos modelos**, esforço, funções, alternativas autorizadas e verificações efetuadas. Não basta escrever somente “Luna” ou “SOL”.

Inicie Codex no repositório consumidor e solicite **somente** o bootstrap inicialmente:

~~~text
Leia CODEX_HANDOFF.md e as seções relevantes de PLAN_INDEX.md.
Confirme repositório/HEAD, versão do Codex, AGENTS.md e configurações.
Execute apenas Agent Bootstrap e Compatibility Gate.
Crie ou integre as configurações aprovadas em .codex/agents/
e .codex/config.toml, preservando arquivos e ajustes existentes.
Verifique os modelos reais, esforços, ferramentas, permissões
e delegação com contexto mínimo. Não inicie os GOALs ainda.
Se precisar de uma nova sessão, registre o checkpoint e informe.
~~~

Quando autorizado e necessário, o bootstrap poderá criar `AGENTS.md`, `.codex/config.toml` e agentes em `.codex/agents/` no **repositório consumidor**.

Arquivo TOML válido não prova que o cliente realmente usou o modelo pretendido. O Compatibility Gate deve testar a configuração e registrar limitações. Se SOL não estiver disponível, não substitua silenciosamente.

## 5. Execute o GOAL

Depois de validar o ambiente:

~~~text
Inicie o GOAL G01 do CODEX_HANDOFF.md atual.
Luna é o orquestrador e implementador principal.
Implemente grandes partes coerentes com o código dos planos.
Delegue só tarefas independentes úteis ou bloqueios comprovados,
sempre com contexto mínimo e limites explícitos.
Teste os resultados essenciais no fim do lote/GOAL,
não cada Plan Part. Reutilize testes aprovados enquanto
código/dependências/configuração relevantes não mudarem.
Se falhar, corrija e repita só os testes afetados.
Comprove Expected Evidence no estado final pertinente.
Respeite arquitetura e arquivos autorizados.
Não solicite trocas manuais de modelo durante o GOAL.
~~~

Luna implementa lotes coerentes e corrige falhas normais sem escalonar imediatamente. Testes antecipados ficam reservados a contratos fundamentais ou riscos altos. Testes anteriormente aprovados só devem ser repetidos quando o código coberto, suas dependências relevantes ou o ambiente/configuração mudarem; após uma correção, executar apenas os testes impactados. Quando necessário, chama SOL preferencialmente em modo **Solve Only** (solução para Luna aplicar). **Scoped Implementation** é permitido para um fragmento realmente difícil de implementar.

O especialista pode solicitar arquivos adicionais específicos e justificar a necessidade; Luna só autoriza ampliação operacional dentro dos limites já aprovados.

Pausas podem ocorrer por permissões, limitações da plataforma, nova sessão necessária ou decisão arquitetural genuína. Retomar uma sessão pausada não é o mesmo que trocar manualmente de modelo.

## 6. Validação e encerramento

Ao concluir um GOAL, Luna apresenta evidências objetivas: arquivos alterados, integrações, testes, Expected Evidence, chamadas a subagentes e limitações. Números de tokens e modelo realmente utilizado só devem ser relatados quando houver dados confiáveis.

O ChatGPT faz o **Convergence Check**, comparando código real e requisitos aprovados. Após convergência, prepara o `CODEX_CLEAN_HANDOFF.md`. A limpeza exige **novo início explícito** do usuário; não é automática.

## 7. Continuidade e segurança

Em um novo chat, leia o manual e os arquivos atuais necessários (`PROJECT.md`, `CHAT_HANDOFF.md`, `MASTER_PLAN.md`, `PLAN_INDEX.md` e apenas Plan Parts relevantes). Nunca trate a memória como fonte de verdade.

**Manual Mode:** uma operação substancial coerente por comando. **Continuous Mode:** execução opt-in com checkpoints e verificação de segurança do contexto, sem importar automaticamente a contagem antiga de 12 operações.

A delegação com contexto mínimo **não é sandbox de arquivos**. Permissões reais, worktrees e outras medidas técnicas podem ser necessárias. Respeite limites de uso, segurança e autorização.

## Licença

[Creative Commons Attribution 4.0 International (CC BY 4.0)](../LICENSE). Detalhes operacionais e fontes oficiais permanecem em [WORKFLOW.md](WORKFLOW.md).
