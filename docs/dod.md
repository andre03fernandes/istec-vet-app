# Definition of Done

> E1 · Parte 6. A Definition of Done (DoD) da equipa: a descrição formal do estado em que o trabalho tem de estar para fazer parte do incremento.
> **Se não cumpre a DoD, não está feito.** Trabalho "quase terminado" não conta para o incremento nem para o Sprint Review.

## 1. O que é e como se relaciona com o resto

- A DoD é o **compromisso do Incremento** no Scrum Guide 2020, tal como o Product Goal é o compromisso do Product Backlog e o Sprint Goal o do Sprint Backlog (ver [processo.md](processo.md#31-artefactos-e-compromissos)).
- Os **critérios de aceitação** são de cada história (ver [backlog.md](backlog.md#5-critérios-de-aceitação)). **A DoD aplica-se a todas.** Uma história pode cumprir os seus critérios e mesmo assim não estar feita, por exemplo se o código não foi revisto por outro elemento.
- A DoD é garantida pelos **Developers** (os quatro elementos), não pelo PO nem pelo SM. O responsável de testes e qualidade (RT) verifica-a antes de cada entrega.
- Como o código é gerado por IA, a DoD inclui **rever o que a IA gerou** (sessão 4, "Agile na era da IA").

## 2. DoD de uma história (sprints de construção)

Uma história de utilizador só está **feita** quando:

**Comportamento**

- [ ] Todos os critérios de aceitação da história foram verificados.
- [ ] Os testes automáticos que implementam os casos de teste do E3 para esta história existem e **passam**, localmente e na integração contínua.
- [ ] Os testes de toda a solução continuam a passar (sem regressões).

**Testes antes do código** (riscos R06 e R01)

- [ ] Os testes foram escritos a partir do plano de testes do E3 e entraram num commit **anterior** ao código de produção.
- [ ] Nenhum valor esperado de um teste do E3 foi alterado no mesmo pull request que altera o código de produção sem justificação escrita no pull request.
- [ ] Os casos-limite da história (valores-limite do E3) estão cobertos, não só o caminho feliz.

**Revisão humana do código gerado pela IA** (risco R04)

- [ ] O código gerado pela IA foi **lido e percebido** por uma pessoa do grupo.
- [ ] O pull request foi revisto e aprovado por **outro** elemento, que sabe explicar o código e indicar o teste que o prova.
- [ ] O código não acrescenta funcionalidades fora da história nem da lista "fora do âmbito" ([visao.md](visao.md#62-fora-do-âmbito)) (risco R05).

**Regras técnicas e de segurança**

- [ ] A hora é obtida através de `TimeProvider` e nunca com `DateTime.Now` (risco R07).
- [ ] Os pacotes novos foram verificados no nuget.org (nome exato, autor, downloads, licença compatível com MIT) e justificados no pull request (riscos R02 e R16).
- [ ] Não há consultas SQL montadas com texto do utilizador, o texto mostrado no ecrã é codificado e a análise estática não tem avisos de segurança novos (risco R15).
- [ ] Não há dados pessoais reais, chaves de API nem palavras-passe no código, nos dados de demonstração ou nos prompts (risco R03).

**Rastreabilidade e registos**

- [ ] A matriz de rastreabilidade liga requisito → design → caso de teste → código.
- [ ] Os defeitos da IA encontrados durante a história estão registados (falta, erro ou falha; forma de deteção; correção).
- [ ] As interações com a IA relevantes estão no diário de engenharia (entregue no E4).
- [ ] A documentação afetada (requisitos, diagramas, README) foi atualizada.

**Integração**

- [ ] O pull request foi integrado em `main` com a integração contínua verde.

## 3. DoD de um documento (sprints de especificação)

Os sprints E1, E2 e E3 produzem documentos, não código. Um documento só está feito quando:

- [ ] Cobre tudo o que o enunciado e as aulas pedem para essa parte da entrega, com o nome de ficheiro indicado pelo docente.
- [ ] Está em Markdown em `docs/`, com os diagramas em texto (Mermaid).
- [ ] Usa os termos do glossário ([visao.md](visao.md#8-glossário)) sempre com o mesmo significado, porque o documento é contexto para a IA.
- [ ] Não tem frases genéricas que serviriam a qualquer projeto: cada decisão está justificada com um facto do nosso contexto.
- [ ] Não tem critérios vagos ("rápido", "fácil", "intuitivo"): cada critério diz como se verifica.
- [ ] Foi lido por **outro** elemento além do autor.
- [ ] O texto proposto pela IA foi revisto pelo grupo antes de entrar no documento.
- [ ] Os links para outros documentos funcionam.
- [ ] Só contém dados fictícios; os únicos nomes reais são os da equipa.
- [ ] Foi enviado para o repositório pelo seu autor, com commit próprio (risco R12).

## 4. Como a DoD é verificada

| Onde | Como | Quem |
|------|------|------|
| Pull request | O modelo de pull request (item T04 do backlog) tem esta lista como checklist; o revisor só aprova com tudo assinalado. | Revisor |
| Integração contínua | A pipeline compila o projeto e corre todos os testes em cada pull request; sem CI verde não há merge. | Automático (configurada pelo RR) |
| Sprint Review | Só se demonstra o que cumpre a DoD. | Equipa |
| Antes de cada entrega | Verificação da DoD de documentos em todos os ficheiros da entrega. | RT |

## 5. Evolução

Esta é a versão inicial, entregue no E1. A DoD é revista em cada **Sprint Retrospective**: quando um defeito da IA passa pela revisão, acrescenta-se o item que o teria apanhado. A versão usada na construção é confirmada no E3, quando o repositório fica pronto a receber código.
