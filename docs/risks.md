# Registo de riscos

> E1 · Parte 3. Um risco é um acontecimento incerto que, se acontecer, prejudica o projeto ou o produto. Um problema que já aconteceu não é um risco.
> Seguimos as quatro etapas da sessão 3: **identificação → análise (probabilidade × impacto) → planeamento da mitigação → monitorização**.

## 1. Escalas

**Probabilidade:** Baixa (pouco provável durante o projeto) · Média (pode acontecer) · Alta (é de esperar que aconteça se nada for feito).

**Impacto:**

- **Insignificante:** atrasa umas horas; nenhuma entrega fica em causa.
- **Moderado:** obriga a refazer trabalho ou faz perder pontos numa entrega.
- **Catastrófico:** compromete uma entrega, os testes do E4 ou a nota individual de um elemento (até zero), ou é uma situação de fraude ou ilegalidade.

**Nível** (matriz da sessão 3):

| Probabilidade \ Impacto | Insignificante | Moderado | Catastrófico |
|---|---|---|---|
| **Alta** | Média | Alta | Alta |
| **Média** | Baixa | Média | Alta |
| **Baixa** | Baixa | Baixa | Média |

Os riscos de nível **Alto** têm plano de mitigação, dono e gatilho. Os de nível **Baixo** são só monitorizados.

**Respostas:** Evitar (mudar o plano para eliminar o risco) · Mitigar (reduzir a probabilidade ou o impacto) · Transferir (passar o impacto a terceiros) · Aceitar (assumir o risco e preparar uma contingência).

**Donos:** papéis da equipa definidos em [process.md](process.md#5-papéis): **PO** (Product Owner — Diogo Consciência), **SM** (Scrum Master — Wilson Amorim), **RT** (responsável de testes e qualidade — Miguel Cruz), **RR** (responsável do repositório e da integração contínua — André Fernandes).

## 2. Registo

A coluna **IA** marca os riscos que nascem do uso de IA para gerar código ou texto (o enunciado exige pelo menos dois; temos nove).

| ID | Risco | IA | Tipo | Prob. | Imp. | Nível | Resposta | Dono | Nível residual |
|----|-------|:--:|------|-------|------|-------|----------|------|----------------|
| R01 | A IA gera a verificação de **sobreposição de consultas** com erros nos limites (`<` vs. `<=`, consulta que acaba às 20h00, mudança de dia), e o erro passa nos testes "caminho feliz". | ● | Tecnológico | Alta | Moderado | **Alta** | Mitigar | RT | Média |
| R02 | A IA sugere **pacotes NuGet ou métodos que não existem**, ou que são de outra versão do .NET / Entity Framework, e o projeto não compila ou instala um pacote malicioso com nome parecido. | ● | Tecnológico | Média | Moderado | **Média** | Mitigar | RR | Baixa |
| R03 | **Dados pessoais reais** entram nos prompts ou nos dados de demonstração: por exemplo, a ficha do animal de um elemento do grupo, ou um NIF e um telefone gerados pela IA que pertencem a pessoas reais. | ● | Legal | Média | Catastrófico | **Alta** | Evitar | PO | Média |
| R04 | **Confiança excessiva** (automation bias): o código gerado é aceite sem ser percebido, e na defesa um elemento não consegue explicar um excerto nem indicar o teste que o prova. | ● | Equipa | Alta | Catastrófico | **Alta** | Mitigar | SM | Média |
| R05 | A IA **acrescenta funcionalidades fora do âmbito** (faturação, lembretes por SMS, login completo) ao gerar requisitos ou código. Esse código fica sem testes e sem rastreabilidade. | ● | Âmbito | Alta | Moderado | **Alta** | Evitar | PO | Baixa |
| R06 | A IA escreve **testes à medida do código que gerou**: os testes passam porque confirmam o comportamento implementado, incluindo os erros, e não o comportamento pedido no E3. | ● | Qualidade | Média | Catastrófico | **Alta** | Mitigar | RT | Média |
| R07 | O código gerado usa a **hora do sistema** diretamente (`DateTime.Now`). Os testes de agenda passam ou falham conforme o dia e a hora a que correm e não se consegue testar "uma consulta às 19h50". | ● | Tecnológico | Média | Moderado | **Média** | Mitigar | RT | Baixa |
| R08 | A **regra de encaixe das urgências** fica ambígua (o que acontece às consultas marcadas quando entra uma urgência emergente?) e cada elemento, ou cada prompt, implementa uma regra diferente. | | Requisitos | Alta | Moderado | **Alta** | Mitigar | PO | Baixa |
| R09 | O **pedido de mudança** chega na aula de 21/01 (turma A) e o **E4 fecha a 22/01**: há 1 dia para analisar o impacto, alterar, atualizar a rastreabilidade e correr os testes de regressão. | | Calendário | Alta | Catastrófico | **Alta** | Mitigar | SM | Média |
| R10 | A **ferramenta de IA fica indisponível** ou o limite do plano gratuito esgota-se perto de um prazo. | ● | Dependência externa | Média | Moderado | **Média** | Mitigar | SM | Baixa |
| R11 | Um **elemento fica indisponível** uma ou mais semanas (trabalho, doença, ou novas suspensões de aulas como a do alerta vermelho de 11 e 12/11). | | Equipa | Média | Moderado | **Média** | Aceitar | SM | Média |
| R12 | O **histórico do Git não reflete o trabalho de cada um**: um elemento concentra os commits (por exemplo, quem tem a ferramenta de IA aberta faz commit de tudo). Como o Git conta para a nota individual, os outros podem ter nota inferior à do grupo. | | Processo | Média | Catastrófico | **Alta** | Mitigar | RR | Baixa |
| R13 | Dois elementos geram código em paralelo com IA e o agente **reescreve ficheiros inteiros** (modelo de dados, `DbContext`, migrações), criando conflitos de merge e esquemas de base de dados divergentes. | ● | Tecnológico | Média | Moderado | **Média** | Mitigar | RR | Baixa |
| R14 | **Perda de trabalho** local não enviado para o repositório (avaria do portátil, ficheiro apagado). | | Tecnológico | Baixa | Moderado | **Baixa** | Transferir | Todos | Baixa |

### Mapa dos riscos na matriz

| Probabilidade \ Impacto | Insignificante | Moderado | Catastrófico |
|---|---|---|---|
| **Alta** | — | R01, R05, R08 | **R04, R09** |
| **Média** | — | R02, R07, R10, R11, R13 | R03, R06, R12 |
| **Baixa** | — | R14 | — |

**Riscos prioritários:** R09 (pedido de mudança em cima do prazo), R04 (não saber explicar o código), R01 (sobreposição nos limites) e R08 (regra das urgências). Os quatro tocam no que o projeto mais valoriza: testes, mudança sem regressões e defesa individual.

## 3. Plano de mitigação

### R01 — Sobreposição de consultas errada nos limites (IA)

- **Porque é concreto:** a regra "duas consultas não se sobrepõem" tem pelo menos quatro casos-limite que a IA trata de forma inconsistente: fim de uma consulta igual ao início da outra (não é conflito), consulta totalmente contida noutra, consulta que ultrapassa o fecho às 20h00 e consulta noutro veterinário à mesma hora (não é conflito).
- **Mitigação:**
  1. Definir no glossário que o intervalo é `[início, fim)` (ver [vision.md](vision.md#8-glossário)) e incluir essa definição no prompt.
  2. No E3, desenhar casos de teste por **valores-limite** para a regra (fim = início, fim = início + 1 min, 19h30–20h00, 19h45–20h15).
  3. Escrever esses testes **antes** de pedir o código à IA; o pull request só é aceite com os testes a passar.
- **Gatilho:** um teste de limite falha, ou um defeito desta regra aparece no registo de defeitos da IA.
- **Contingência:** escrever a função de verificação à mão, isolada e com os testes do E3, e registar o defeito.

### R02 — Dependências ou APIs inventadas (IA)

- **Mitigação:** fixar no ficheiro de contexto da IA a versão do .NET e a lista de pacotes permitidos. Cada pacote novo é verificado no nuget.org (nome exato, autor, número de downloads) antes de ser instalado, e é justificado no pull request. A integração contínua compila o projeto em cada pull request.
- **Gatilho:** erro de compilação "type or namespace not found", ou um pacote com poucos downloads.
- **Contingência:** pedir à IA a solução só com a biblioteca base do .NET.

### R03 — Dados pessoais reais (IA, legal)

- **Resposta: Evitar.**
  - Os dados de demonstração vêm de um único ficheiro de *seed* revisto pelo grupo. Os nomes são inventados, os telefones usam um padrão impossível (por exemplo, `900 000 0xx`), os emails usam o domínio reservado `@example.com` e não há NIF.
  - Regra de equipa: nunca colar fichas, receitas ou fotografias reais em prompts, mesmo de animais próprios.
  - Na checklist do pull request: "Não contém dados pessoais reais nem segredos."
- **Gatilho:** um revisor encontra um dado que parece real.
- **Contingência:** apagar o dado num novo commit (o histórico não é reescrito), avisar o docente e registar o incidente.

### R04 — Código aceite sem ser percebido (IA)

- **Mitigação:**
  1. Todo o código entra por **pull request revisto por outro elemento**. O revisor tem de conseguir explicar o código e indicar o teste que o cobre; se não conseguir, não aprova.
  2. Os pares autor/revisor rodam em cada sprint, para que todos revejam código de todas as áreas.
  3. Antes da defesa: cada elemento explica aos outros um excerto escolhido ao acaso (simulação da pergunta 1 da defesa).
  4. O diário de engenharia regista porque é que cada resposta da IA foi aceite, alterada ou rejeitada.
- **Gatilho:** um pull request é aprovado sem comentários ou em menos de 5 minutos para mais de 100 linhas.
- **Contingência:** sessão de revisão conjunta desse código.

### R05 — Funcionalidades fora do âmbito (IA)

- **Resposta: Evitar.** A lista "fora do âmbito" de [vision.md](vision.md#62-fora-do-âmbito) entra em todos os prompts. Só se gera código para histórias do sprint corrente. Código sem história no backlog não entra no ramo principal. Os requisitos que a IA propuser e o grupo rejeitar alimentam a secção "requisitos rejeitados" do E2.
- **Gatilho:** aparecem no diff ficheiros ou classes que nenhuma história pede.

### R06 — Testes feitos à medida do código (IA)

- **Mitigação:** os casos de teste vêm da tabela do plano de testes (E3), com valores de entrada e resultados esperados escritos pelo grupo. O código de teste entra **num commit antes** do código de produção (o teste começa a falhar). Uma asserção do E3 não pode ser alterada no mesmo pull request que altera o código de produção sem justificação escrita. O RT confere a correspondência teste ↔ caso de teste da matriz de rastreabilidade.
- **Gatilho:** um teste muda o valor esperado no mesmo pull request que corrige o código.

### R07 — Testes dependentes da hora do sistema (IA)

- **Mitigação:** decisão de arquitetura (ADR no E3) de obter a hora sempre através de uma abstração injetável (`TimeProvider` do .NET), nunca com `DateTime.Now`. Fica escrita no ficheiro de contexto da IA e é verificada na revisão (procurar `DateTime.Now` no diff).
- **Gatilho:** um teste falha só a certas horas ou só na integração contínua.

### R08 — Regra das urgências ambígua

- **Porque é concreto:** é a dificuldade indicada no enunciado para este domínio. Há pelo menos três regras possíveis: (a) a urgência vai para o veterinário livre e não mexe na agenda; (b) a urgência emergente interrompe e as consultas seguintes atrasam; (c) há blocos reservados para urgências (conflito C1 em [stakeholders.md](stakeholders.md#5-conflitos-previsíveis)).
- **Mitigação:** no E2, escolher **uma** regra, escrevê-la como regra de negócio com critérios de aceitação e validá-la com o docente. Se a discussão não fechar, um wireframe do ecrã da fila de urgências ajuda a decidir (prototipagem descartável, só para esta parte).
- **Gatilho:** no E2, a regra ainda tem "depende" ou "normalmente".

### R09 — Pedido de mudança 1 dia antes do E4

- **Porque é concreto:** com o calendário atualizado, o pedido de mudança é entregue na sessão 11 (21/01, turma A) e o E4 fecha a 22/01. Não há tempo para estudar o código nessa altura.
- **Mitigação:**
  1. **Sprint 1 fecha antes da sessão 11**: os casos de uso do E4 já estão feitos e testados quando o pedido chega (ver [process.md](process.md#4-calendário)).
  2. **Matriz de rastreabilidade** sempre atualizada: a análise de impacto faz-se a partir da matriz, não do código.
  3. **Testes automáticos e integração contínua** desde o primeiro pull request: os testes de regressão correm sozinhos.
  4. Regras de negócio configuráveis (duração das consultas, blocos de urgência, horários), para que uma mudança provável seja de configuração e não de código.
  5. Ensaio: na sessão 10 (14/01), o grupo inventa um pedido de mudança e mede quanto tempo leva a fazer a análise de impacto.
- **Gatilho:** a 14/01 há histórias do sprint 1 por terminar.
- **Contingência:** entregar a análise de impacto completa e a mudança implementada parcialmente, com os testes de regressão a passar, em vez de uma mudança completa que quebra testes.

### R10 — Ferramenta de IA indisponível ou sem quota (IA)

- **Mitigação:** usar como ferramenta principal uma que seja gratuita para todos (GitHub Copilot via GitHub Education) e ter uma segunda ferramenta configurada. Os artefactos (requisitos, diagramas, testes) estão em Markdown, por isso funcionam como contexto em qualquer ferramenta. Não deixar a geração de código para as 48 horas antes de um prazo.

### R11 — Elemento indisponível

- **Resposta: Aceitar, com contingência.** Nenhuma área tem um único dono: cada história tem autor e revisor diferentes. A contingência é redistribuir as histórias no início da semana seguinte e reduzir o âmbito do sprint pelo fundo do backlog (histórias "Could"), nunca pelo topo.

### R12 — Histórico do Git desequilibrado

- **Mitigação:** cada elemento trabalha em ramos próprios e faz os seus commits, incluindo os de documentação (cada um escreve as partes que lhe estão atribuídas). Os pull requests são abertos por quem fez o trabalho. O RR verifica a distribuição dos commits no fim de cada sprint.
- **Gatilho:** no fim de um sprint, um elemento tem menos de 15% dos commits.

### R13 — Conflitos de merge provocados por agentes de IA (IA)

- **Mitigação:** uma história por ramo e pull requests pequenos. As alterações ao modelo de dados e às migrações são feitas por um elemento de cada vez, avisando no canal da equipa. Os prompts limitam os ficheiros que o agente pode alterar.

### R14 — Perda de trabalho local

- **Resposta: Transferir** o armazenamento para o GitHub, com push no fim de cada sessão de trabalho, mesmo de trabalho incompleto em ramo próprio.

## 4. Análise SWOT (de onde vieram os riscos)

| | Positivo | Negativo |
|---|---|---|
| **Interno** | **Forças:** domínio fácil de perceber (todos já levaram ou conhecem quem leve um animal ao veterinário); âmbito pequeno; regras de agenda testáveis com valores concretos. | **Fraquezas:** regra das urgências por definir (R08); pouca experiência a rever código que não escrevemos (R04, R06); tempo limitado por serem aulas à noite (R11). |
| **Externo** | **Oportunidades:** ferramentas de IA gratuitas para estudantes; `TimeProvider` e frameworks de teste do .NET resolvem o problema da hora (R07); o docente está disponível semanalmente para validar requisitos. | **Ameaças:** calendário comprimido no fim (R09); quotas e mudanças das ferramentas de IA (R10); RGPD e dados reais (R03); suspensões de aulas imprevistas (R11). |

As fraquezas e ameaças alimentaram o registo; as forças e oportunidades estão nas mitigações.

## 5. Monitorização

| Quando | O quê | Quem |
|--------|-------|------|
| Início de cada sprint | Rever probabilidade e impacto de todos os riscos; fechar os que já não se aplicam; acrescentar novos | Equipa (SM conduz) |
| Em cada entrega (E2, E3, E4) | Verificar os gatilhos de R01, R05, R06, R08, R12 | Dono de cada risco |
| Revisão de cada pull request | Checklist: dados fictícios (R03), sem `DateTime.Now` (R07), pacotes verificados (R02), testes antes do código (R06), revisor sabe explicar (R04) | Revisor |
| 14/01/2027 | Ponto de controlo do R09: o sprint 1 está fechado? | SM |
| 21/01/2027 | Pedido de mudança: análise de impacto pela matriz de rastreabilidade | Equipa |

Os defeitos encontrados no código gerado (E4) são registados à parte, em `docs/ai-defects.md`. Quando um defeito confirma um risco (por exemplo, R01), o risco é atualizado aqui.
