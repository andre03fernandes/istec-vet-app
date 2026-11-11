# Documentação do projeto — istec-vet-app

Sistema de gestão de uma clínica veterinária: marcação de consultas por veterinário, urgências e ficha clínica do animal.
Projeto de Engenharia de Software Assistida por IA (ISTEC, 2026/2027) · 3.º ano, pós-laboral, turma A.

## Equipa

| Elemento | Papel |
|----------|-------|
| Diogo Consciência | Product Owner (PO) |
| Wilson Amorim | Scrum Master (SM) |
| Miguel Cruz | Responsável de testes e qualidade (RT) |
| André Fernandes | Responsável do repositório e da integração contínua (RR) |

Todos os elementos são também *developers*. As responsabilidades de cada papel estão em [process.md](process.md#5-papéis).

## E1 — Visão e plano (entrega: 22/11/2026)

| # | Parte | Documento |
|---|-------|-----------|
| 1 | Visão do sistema: problema, utilizadores e o que fica fora do âmbito | [vision.md](vision.md) |
| 2 | Análise de stakeholders e dos seus interesses | [stakeholders.md](stakeholders.md) |
| 3 | Registo de riscos (probabilidade, impacto, mitigação; inclui riscos de IA) | [risks.md](risks.md) |
| 4 | Modelo de processo escolhido e comparação com alternativas | [process.md](process.md) |
| 5 | Product backlog inicial, com histórias priorizadas | [backlog.md](backlog.md) |

## Próximas entregas

| Entrega | Prazo | Onde vai ficar |
|---------|-------|----------------|
| E2 — Requisitos e casos de uso | 06/12/2026 | `docs/requirements.md`, `docs/use-cases.md`, `docs/traceability.md` |
| E3 — Design e plano de testes | 10/01/2027 | `docs/architecture.md`, `docs/adr/`, `docs/test-plan.md` |
| E4 — Sistema final | 22/01/2027 | código, testes, `docs/ai-defects.md`, `docs/engineering-log.md` |

## Regras que seguimos em todos os documentos

- **Dados fictícios.** Todos os dados do domínio (clínica, funcionários, tutores, animais e contactos) são inventados; os únicos nomes reais são os da equipa, nesta página e nos papéis. Fora isso, nenhum dado pessoal real entra nos documentos, nos prompts ou no sistema.
- **Diagramas em texto** (Mermaid), para poderem ser versionados e dados à IA como contexto.
- **Os documentos são o prompt.** Estes ficheiros são o contexto que damos à IA quando gera código. Por isso, cada termo do domínio é usado sempre com o mesmo significado (ver o glossário em [vision.md](vision.md#8-glossário)).
