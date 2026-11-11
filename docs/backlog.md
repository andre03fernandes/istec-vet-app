# Product backlog inicial

> E1 · Parte 5. Histórias de utilizador priorizadas. Os critérios de aceitação aqui são um esboço: no E2 passam a requisitos numerados, com critérios de aceitação verificáveis.
> Formato: **Como** \<perfil\>, **quero** \<ação\>, **para** \<benefício\>.

## 1. Como priorizámos

A ordem do backlog segue três critérios, por esta ordem:

1. **Valor para os stakeholders do quadrante "gerir de perto"** (diretora clínica e veterinários, ver [stakeholders.md](stakeholders.md#3-matriz-poder-interesse)): resolver os problemas P1 a P4 da [visão](vision.md#2-problema).
2. **Risco primeiro:** as histórias com mais incerteza ou mais risco de defeitos da IA sobem, para os problemas aparecerem cedo e não na semana do pedido de mudança. É o caso da sobreposição de consultas (R01) e das urgências (R08).
3. **Dependências:** uma história que outra precisa vem antes (não há histórico sem notas clínicas, nem marcação sem animais).

Classificação **MoSCoW**: **Must** (sem isto o sistema não resolve o problema), **Should** (importante, entra se houver tempo no sprint 1), **Could** (desejável), **Won't** (fora do âmbito desta versão, ver [vision.md](vision.md#62-fora-do-âmbito)).

Estimativa em **pontos de história** (1, 2, 3, 5, 8), relativa à US01 = 8 (a história mais complexa).

## 2. Épicos

| Épico | Descrição | Problema que resolve |
|-------|-----------|----------------------|
| EP1 | Tutores e animais | Base para tudo o resto |
| EP2 | Agenda por veterinário | P1 — marcações sobrepostas |
| EP3 | Urgências | P2 — urgências desorganizam a agenda |
| EP4 | Ficha clínica e histórico | P3 — histórico disperso; P4 — registos sem rasto |
| EP5 | Transversal | Perfis de utilizador |

## 3. Backlog ordenado

| Ordem | ID | Épico | História | Prioridade | Pontos | Caso de uso candidato |
|:-----:|----|-------|----------|:----------:|:------:|-----------------------|
| 1 | US01 | EP2 | Como **rececionista**, quero **marcar uma consulta para um animal com um veterinário numa hora livre**, para que **nenhum veterinário tenha consultas sobrepostas**. | Must | 8 | UC1 Marcar consulta |
| 2 | US02 | EP1 | Como **rececionista**, quero **registar um tutor e os seus animais**, para **poder marcar consultas para eles**. | Must | 3 | UC5 Registar tutor e animal |
| 3 | US03 | EP2 | Como **veterinário**, quero **ver a minha agenda de um dia, ordenada por hora**, para **saber que animais vou ver e quando**. | Must | 3 | UC1 Marcar consulta |
| 4 | US04 | EP3 | Como **rececionista**, quero **registar a chegada de uma urgência**, para que **fique na fila a aguardar triagem**. | Must | 3 | UC2 Gerir urgência |
| 5 | US05 | EP3 | Como **enfermeiro**, quero **atribuir um nível de triagem a uma urgência**, para que **a fila fique ordenada por prioridade clínica**. | Must | 5 | UC2 Gerir urgência |
| 6 | US06 | EP3 | Como **veterinário**, quero **atender a próxima urgência da fila**, para que **os casos mais graves sejam vistos primeiro**. | Must | 5 | UC2 Gerir urgência |
| 7 | US07 | EP4 | Como **veterinário**, quero **registar a nota clínica de uma consulta e fechá-la**, para que **fique no histórico do animal e já não possa ser alterada**. | Must | 5 | UC3 Registar consulta |
| 8 | US08 | EP4 | Como **veterinário**, quero **ver o histórico cronológico de um animal, com as alergias em destaque**, para **decidir o tratamento com toda a informação**. | Must | 5 | UC4 Consultar histórico |
| 9 | US18 | EP5 | Como **utilizador**, quero **escolher o meu perfil ao entrar** (rececionista, enfermeiro, veterinário, diretora), para **ver só as ações que o meu perfil pode fazer**. | Should | 2 | — (suporta UC2 e UC3) |
| 10 | US09 | EP2 | Como **rececionista**, quero **cancelar ou reagendar uma consulta**, para **libertar a vaga quando o tutor não pode vir**. | Should | 5 | UC1 (extensão) |
| 11 | US10 | EP4 | Como **veterinário**, quero **acrescentar uma adenda a uma nota fechada**, para **corrigir um registo sem apagar o original**. | Should | 3 | UC3 (extensão) |
| 12 | US12 | EP2 | Como **rececionista**, quero **marcar falta quando o tutor não aparece**, para que **a consulta não fique "marcada" para sempre**. | Should | 2 | UC1 (extensão) |
| 13 | US13 | EP1 | Como **rececionista**, quero **pesquisar um animal pelo nome, pelo nome do tutor ou pelo microchip**, para **encontrar a ficha depressa, com o telefone na mão**. | Should | 3 | UC5 (extensão) |
| 14 | US11 | EP2 | Como **rececionista**, quero que **o sistema proponha a próxima vaga livre do veterinário habitual do animal**, para **marcar mais depressa e manter o mesmo veterinário** (conflito C4). | Should | 5 | UC1 (extensão) |
| 15 | US15 | EP2 | Como **diretora clínica**, quero **reservar blocos de urgência por veterinário e por dia**, para **equilibrar a ocupação da agenda com a capacidade de resposta a urgências** (conflito C1). | Could | 5 | UC2 |
| 16 | US14 | EP2 | Como **diretora clínica**, quero **definir o horário de trabalho de cada veterinário**, para que **só se marquem consultas dentro desse horário**. | Could | 5 | — |
| 17 | US16 | EP2 | Como **diretora clínica**, quero **ver a agenda de todos os veterinários num dia**, para **acompanhar a ocupação da clínica**. | Could | 3 | — |
| 18 | US17 | EP4 | Como **veterinário**, quero **registar uma vacina com a data da próxima dose**, para **saber quando o animal deve voltar**. | Could | 3 | — |
| — | W01 | — | Como **tutor**, quero **receber um lembrete por SMS ou email** antes da consulta. | Won't | — | Fora do âmbito |
| — | W02 | — | Como **tutor**, quero **marcar consultas num portal ou numa app**. | Won't | — | Fora do âmbito |
| — | W03 | — | Como **rececionista**, quero **emitir a fatura da consulta**. | Won't | — | Fora do âmbito |
| — | W04 | — | Como **veterinário**, quero **passar uma receita eletrónica e dar baixa do stock**. | Won't | — | Fora do âmbito |
| — | W05 | — | Como **utilizador**, quero **entrar com email e palavra-passe**. | Won't | — | Fora do âmbito (US18 simplifica) |
| — | W06 | — | Como **veterinário**, quero **exportar o histórico do animal para PDF**. | Won't | — | Fora do âmbito |

**Totais:** Must = 37 pontos (sprint 1) · Should = 20 pontos (entram no sprint 1 se houver capacidade, pela ordem acima) · Could = 16 pontos.

US15 está como *Could*, mas **pode subir a Must** se, no E2, a regra das urgências escolhida for "blocos reservados" (ver R08 e conflito C1).

## 4. Critérios de aceitação (esboço) das histórias Must

### US01 — Marcar consulta

- Uma consulta tem animal, veterinário, tipo, início e fim; o fim é calculado a partir da duração do tipo de consulta.
- Uma marcação que se **sobrepõe** a outra consulta ativa do mesmo veterinário é recusada, com mensagem que indica a consulta em conflito.
- Uma consulta que **começa exatamente quando outra acaba** é aceite (intervalo `[início, fim)`).
- A mesma hora com **outro veterinário** é aceite.
- Uma consulta que começa ou acaba **fora do horário** do veterinário (por exemplo, 19h45–20h15 com fecho às 20h00) é recusada.
- Uma consulta no **passado** é recusada.
- Uma consulta acabada de marcar fica no estado *Marcada*.

### US02 — Registar tutor e animal

- Um animal pertence sempre a um tutor; não se cria um animal sem tutor.
- Campos obrigatórios do animal: nome, espécie (de uma lista fechada) e tutor. Data de nascimento, raça, microchip e alergias são opcionais.
- O número de microchip, se existir, tem 15 dígitos e é único no sistema.

### US03 — Agenda diária do veterinário

- Mostra só as consultas desse veterinário e desse dia, por ordem de hora de início.
- Mostra o estado de cada consulta; as canceladas aparecem assinaladas ou ocultas (a decidir no E2).

### US04 — Registar chegada de urgência

- Regista o animal (ou cria um registo mínimo se o animal ainda não existir), o motivo e a hora de chegada (dada pelo relógio do sistema).
- A urgência fica no estado *Aguarda triagem*.

### US05 — Triagem

- Só os perfis enfermeiro e veterinário podem atribuir o nível de triagem (conflito C3).
- Há 3 níveis; a fila ordena por nível (mais grave primeiro) e, no mesmo nível, por hora de chegada.

### US06 — Atender urgência

- O veterinário retira da fila a urgência de topo, que passa a *Em atendimento* com esse veterinário.
- O efeito na agenda do veterinário segue a regra de encaixe decidida no E2 (R08).

### US07 — Nota clínica

- Uma nota clínica tem motivo, observações, diagnóstico e tratamento, e fica associada à consulta ou urgência.
- Enquanto está aberta, pode ser editada pelo veterinário que a criou.
- Ao fechar a nota, a consulta passa a *Concluída*. A nota fechada não pode ser alterada nem apagada (ver US10 para correções).

### US08 — Histórico do animal

- Lista consultas, urgências, notas e adendas do animal por ordem cronológica, da mais recente para a mais antiga.
- As alergias registadas aparecem no topo, sempre visíveis.
- Para cada registo, mostra a data, o veterinário e o tipo.

## 5. Itens técnicos (não são histórias, mas entram no planeamento)

| ID | Item | Quando | Ligação |
|----|------|--------|---------|
| T01 | Projeto base .NET com projeto de testes, a compilar e a correr na integração contínua (GitHub Actions) | E3 (repositório pronto a receber código) | R02, R09 |
| T02 | Ficheiro de dados de demonstração fictícios (tutores, animais, veterinários, horários), revisto pelo grupo | Início do sprint 1 | R03 |
| T03 | Ficheiro de contexto para a IA (stack, versões, regras: `TimeProvider`, pacotes permitidos, exclusões de âmbito) | Fim do E3 | R02, R05, R07 |
| T04 | Modelo de pull request com a checklist da Definition of Done | E3 | R04, R06, R12 |

## 6. Candidatos aos 3 a 5 casos de uso a implementar

A seleção final é feita no E2. A proposta inicial cobre as três dificuldades do domínio (agenda por veterinário, urgências e histórico):

| Caso de uso | Histórias | Dificuldade do domínio coberta |
|-------------|-----------|--------------------------------|
| UC1 Marcar consulta | US01, US03 | Agenda por veterinário |
| UC2 Gerir urgência | US04, US05, US06 | Urgências |
| UC3 Registar consulta | US07 | Histórico (escrita) |
| UC4 Consultar histórico do animal | US08 | Histórico (leitura) |
| UC5 Registar tutor e animal | US02 | Pré-condição dos restantes |

Se o tempo apertar, o UC5 pode ficar reduzido aos dados de demonstração (T02), mantendo os quatro casos de uso que cobrem as dificuldades do domínio.

## 7. Manutenção do backlog

- O PO reordena o backlog no início de cada sprint, com base no feedback do docente e no registo de riscos.
- Uma história nova proposta pela IA só entra se o PO a aceitar; se for rejeitada, fica registada nos requisitos rejeitados do E2.
- Quando chegar o pedido de mudança, entra como história nova no topo do sprint 2, com análise de impacto feita a partir da matriz de rastreabilidade.
