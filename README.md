# istec-vet-app

A veterinary clinic management system developed as a Software Engineering project at ISTEC, featuring appointment scheduling, emergency triage, and medical records management.

Sistema de gestão de uma clínica veterinária (fictícia): marcação de consultas por veterinário sem sobreposições, fila de urgências por nível de triagem e histórico clínico do animal. Projeto de Engenharia de Software Assistida por IA (ISTEC, 2026/2027) · 3.º ano, pós-laboral, turma A.

## Equipa

| Elemento | Responsabilidade na Scrum Team |
|----------|--------------------------------|
| Diogo Consciência | Product Owner (PO) · Developer |
| Wilson Amorim | Scrum Master (SM) · Developer |
| Miguel Cruz | Developer · responsável de testes e qualidade (RT) |
| André Fernandes | Developer · responsável do repositório e da integração contínua (RR) |

Todos os elementos são *Developers*. RT e RR são responsabilidades adicionais dentro dos Developers, não papéis do Scrum. O que cada uma implica está em [docs/processo.md](docs/processo.md#5-responsabilidades-na-scrum-team).

## Documentação

Toda a documentação está em `docs/`, em Markdown, com os diagramas em Mermaid.

### E1 — Visão e plano (entrega: 22/11/2026)

| # | Parte | Documento |
|---|-------|-----------|
| 1 | Visão do sistema: problema, utilizadores e o que fica fora do âmbito | [docs/visao.md](docs/visao.md) |
| 2 | Análise de stakeholders e dos seus interesses | [docs/stakeholders.md](docs/stakeholders.md) |
| 3 | Registo de riscos (probabilidade, impacto, mitigação; inclui riscos de IA) | [docs/riscos.md](docs/riscos.md) |
| 4 | Modelo de processo escolhido e comparação com alternativas | [docs/processo.md](docs/processo.md) |
| 5 | Product backlog inicial: Product Goal, histórias priorizadas (MoSCoW e tamanho) e critérios de aceitação | [docs/backlog.md](docs/backlog.md) |
| 6 | Definition of Done da equipa | [docs/dod.md](docs/dod.md) |

### Próximas entregas

| Entrega | Prazo | Onde vai ficar |
|---------|-------|----------------|
| E2 — Requisitos e casos de uso | 06/12/2026 | `docs/requisitos.md`, `docs/casos-de-uso.md`, `docs/rastreabilidade.md` |
| E3 — Design e plano de testes | 10/01/2027 | `docs/arquitetura.md`, `docs/adr/`, `docs/plano-testes.md`, versão final de `docs/dod.md` |
| E4 — Sistema final | 22/01/2027 | código, testes, `docs/defeitos-ia.md`, `docs/diario-engenharia.md`, análise de impacto do pedido de mudança |

Os nomes dos ficheiros das próximas entregas podem mudar se o docente indicar outros nas aulas, como aconteceu no E1.

### Regras que seguimos em todos os documentos

- **Dados fictícios.** Todos os dados do domínio (clínica, funcionários, tutores, animais e contactos) são inventados; os únicos nomes reais são os da equipa. Nenhum dado pessoal real entra nos documentos, nos prompts ou no sistema.
- **Diagramas em texto** (Mermaid), para poderem ser versionados e dados à IA como contexto.
- **Os documentos são o prompt.** Estes ficheiros são o contexto que damos à IA quando gera código. Por isso, cada termo do domínio é usado sempre com o mesmo significado (ver o glossário em [docs/visao.md](docs/visao.md#8-glossário)).
- **Cada documento cumpre a [Definition of Done de documentos](docs/dod.md#3-dod-de-um-documento-sprints-de-especificação)** antes de ser entregue.

## Ferramentas de IA usadas

Declaração exigida pelo enunciado: que ferramentas de IA usamos e para quê.

| Ferramenta | Para quê | Em que entregas |
|------------|----------|-----------------|
| **Claude** (Anthropic), através do Claude Code e do claude.ai | Propor rascunhos dos documentos a partir dos materiais das aulas, do enunciado e das decisões do grupo (visão, stakeholders, riscos, processo, backlog, DoD). Rever a coerência entre documentos (datas, nomes, links). Reformular os documentos quando as aulas trazem regras novas. Apoio pontual com Git. Na construção: gerar código e testes a partir dos requisitos, do design e dos casos de teste do grupo. | E1 em diante |

**Porque escolhemos o Claude:**

- **Contexto longo.** O princípio do projeto é que *os artefactos de engenharia são o prompt*. O Claude aceita de uma vez a visão, os requisitos, os diagramas e o plano de testes, por isso a IA gera código com todo o contexto e não só com a história do momento.
- **Trabalha sobre o repositório.** O Claude Code lê e altera os ficheiros do repositório e corre comandos (compilar, correr os testes). Assim, o ciclo *testes do grupo → IA gera → testes passam ou falham* faz-se no mesmo sítio, e cada defeito aparece num diff pequeno.
- **Gratuito para todos os elementos.** O plano gratuito do claude.ai está disponível para todos, como o enunciado exige. Os limites desse plano estão tratados no risco R10 ([docs/riscos.md](docs/riscos.md)), que prevê uma ferramenta alternativa.

**Como usamos a IA:** a IA propõe e o grupo decide. Os testes são desenhados pelo grupo antes de o código ser gerado; todo o código gerado é lido e revisto por outro elemento antes de entrar em `main` (ver a [Definition of Done](docs/dod.md)). Nos sprints de construção, as interações relevantes, e o que foi aceite, alterado ou rejeitado, ficam no diário de engenharia (E4). Não colocamos dados pessoais reais, chaves de API ou palavras-passe nos prompts.

## Como executar

As instruções de execução e de testes são acrescentadas quando existir código (E3/E4).
