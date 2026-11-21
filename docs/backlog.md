# Product backlog inicial

> E1 · Parte 5. Product Goal, histórias de utilizador ordenadas, prioridade MoSCoW, tamanho e critérios de aceitação.
> Formato das histórias: **Como** \<tipo de utilizador\>, **quero** \<objetivo\>, **para** \<benefício\>.
> Formato dos critérios: **Dado** um contexto, **quando** acontece uma ação, **então** espera-se um resultado.
> No E2, as histórias do topo passam a requisitos numerados, com critérios de aceitação verificáveis.

## 1. Product Goal

> **No fim do semestre, a receção e a equipa clínica da Clínica Veterinária Quatro Patas conseguem marcar consultas sem sobreposições por veterinário, ordenar as urgências por prioridade de triagem e consultar o histórico clínico de cada animal sem que nenhum registo fechado possa ser apagado. Tudo isto em 3 a 5 casos de uso testados de ponta a ponta.**

O Product Goal é o compromisso do Product Backlog (Scrum Guide 2020). Cada história abaixo contribui para ele; uma história que não contribui fica *Won't*. Resume os objetivos OB1 a OB5 da [visão](visao.md#4-objetivos-smart).

## 2. Como ordenámos

A ordem do backlog segue três critérios, por esta ordem:

1. **Valor para os stakeholders do quadrante "gerir de perto"** (diretora clínica e veterinários, ver [stakeholders.md](stakeholders.md#3-matriz-poder-interesse)): resolver os problemas P1 a P4 da [visão](visao.md#2-problema).
2. **Risco primeiro:** as histórias com mais incerteza ou mais risco de defeitos da IA sobem, para os problemas aparecerem cedo e não na semana do pedido de mudança. É o caso da sobreposição de consultas (R01) e das urgências (R08).
3. **Dependências:** uma história de que outra precisa vem antes (não há histórico sem notas clínicas, nem marcação sem animais).

**Prioridade MoSCoW:** **Must** (tem de ter: sem isto o sistema não resolve o problema), **Should** (devia ter: entra no sprint 1 se houver capacidade), **Could** (podia ter), **Won't** (não desta vez: fora do âmbito desta versão, ver [visao.md](visao.md#62-fora-do-âmbito)).

**Tamanho:** **P**, **M** ou **G**, por comparação entre histórias:

| Tamanho | Referência | O que significa |
|:-------:|------------|-----------------|
| **P** | H4 (ver a agenda do dia) | Uma regra simples ou só leitura e ordenação de dados. |
| **M** | H1 (marcar consulta sem sobreposição) | Uma regra de negócio com casos-limite, ou uma mudança de estado com restrições. |
| **G** | — | Várias regras ou mais do que cabe num sprint. **Uma história G é partida** antes de entrar no backlog. |

Na primeira versão do backlog, "marcar consulta" era uma só história G: juntava a regra da sobreposição com a regra do horário da clínica e do passado. Foi partida em **H1** e **H2**, que se testam de forma independente. Não ficou nenhuma história G.

## 3. Épicos

| Épico | Descrição | Problema que resolve |
|-------|-----------|----------------------|
| EP1 | Tutores e animais | Base para tudo o resto |
| EP2 | Agenda por veterinário | P1: marcações sobrepostas |
| EP3 | Urgências | P2: urgências desorganizam a agenda |
| EP4 | Ficha clínica e histórico | P3: histórico disperso; P4: registos sem rasto |
| EP5 | Transversal | Perfis de utilizador |

## 4. Backlog ordenado

A coluna **Stakeholder** liga cada história a quem a pede, com os IDs de [stakeholders.md](stakeholders.md#1-identificação). Uma história sem stakeholder não entra no backlog.

A coluna **Critérios** segue o modelo do docente (sessão 4): indica **quantos critérios de aceitação** a história tem e **se já estão escritos**. Por exemplo, "5, escritos" quer dizer que a história tem 5 critérios no formato Dado/quando/então, na [secção 5](#5-critérios-de-aceitação). As histórias *Should* e *Could* ficam com os critérios "por escrever": são escritos no E2, quando a história subir no backlog.

| Ordem | ID | Épico | História | Stakeholder | Prioridade | Tamanho | Critérios |
|:-----:|----|-------|----------|-------------|:----------:|:-------:|-----------|
| 1 | H1 | EP2 | Como **rececionista**, quero **marcar uma consulta para um animal com um veterinário numa hora livre**, para que **nenhum veterinário tenha consultas sobrepostas**. | S3, S2 | Must | M | 5, escritos |
| 2 | H2 | EP2 | Como **rececionista**, quero que **o sistema recuse marcações fora do horário da clínica ou no passado**, para **não marcar consultas que não podem acontecer**. | S3, S1 | Must | P | 4, escritos |
| 3 | H3 | EP1 | Como **rececionista**, quero **registar um tutor e os seus animais**, para **poder marcar consultas para eles**. | S3 | Must | P | 4, escritos |
| 4 | H4 | EP2 | Como **veterinário**, quero **ver a minha agenda de um dia, ordenada por hora**, para **saber que animais vou ver e quando**. | S2 | Must | P | 2, escritos |
| 5 | H5 | EP3 | Como **rececionista**, quero **registar a chegada de uma urgência**, para que **fique na fila a aguardar triagem**. | S3, S4 | Must | P | 2, escritos |
| 6 | H6 | EP3 | Como **enfermeiro**, quero **atribuir um nível de triagem a uma urgência**, para que **a fila fique ordenada por prioridade clínica**. | S4, S2 | Must | M | 4, escritos |
| 7 | H7 | EP3 | Como **veterinário**, quero **atender a próxima urgência da fila**, para que **os casos mais graves sejam vistos primeiro**. | S2 | Must | M | 2, escritos |
| 8 | H8 | EP4 | Como **veterinário**, quero **registar a nota clínica de uma consulta e fechá-la**, para que **fique no histórico do animal e já não possa ser alterada**. | S2, S1, S6 | Must | M | 5, escritos |
| 9 | H9 | EP4 | Como **veterinário**, quero **ver o histórico cronológico de um animal, com as alergias em destaque**, para **decidir o tratamento com toda a informação**. | S2, S4 | Must | M | 3, escritos |
| 10 | H10 | EP5 | Como **funcionário da clínica**, quero **escolher o meu perfil ao entrar** (rececionista, enfermeiro, veterinário, diretora), para **ver só as ações que o meu perfil pode fazer**. | S1, S4 | Should | P | Por escrever (E2) |
| 11 | H11 | EP2 | Como **rececionista**, quero **cancelar ou reagendar uma consulta**, para **libertar a vaga quando o tutor não pode vir**. | S3, S5 | Should | M | Por escrever (E2) |
| 12 | H12 | EP4 | Como **veterinário**, quero **acrescentar uma adenda a uma nota fechada**, para **corrigir um registo sem apagar o original**. | S2, S6 | Should | P | Por escrever (E2) |
| 13 | H13 | EP2 | Como **rececionista**, quero **marcar falta quando o tutor não aparece**, para que **a consulta não fique "marcada" para sempre**. | S3, S1 | Should | P | Por escrever (E2) |
| 14 | H14 | EP1 | Como **rececionista**, quero **pesquisar um animal pelo nome, pelo nome do tutor ou pelo microchip**, para **encontrar a ficha depressa, com o telefone na mão**. | S3 | Should | P | Por escrever (E2) |
| 15 | H15 | EP2 | Como **rececionista**, quero que **o sistema proponha a próxima vaga livre do veterinário habitual do animal**, para **marcar mais depressa e manter o mesmo veterinário** (conflito C4). | S5, S3 | Should | M | Por escrever (E2) |
| 16 | H16 | EP2 | Como **diretora clínica**, quero **reservar blocos de urgência por veterinário e por dia**, para **equilibrar a ocupação da agenda com a capacidade de resposta a urgências** (conflito C1). | S1, S2 | Could | M | Por escrever (E2) |
| 17 | H17 | EP2 | Como **diretora clínica**, quero **definir o horário de trabalho de cada veterinário**, para que **só se marquem consultas dentro desse horário**. | S1 | Could | M | Por escrever (E2) |
| 18 | H18 | EP2 | Como **diretora clínica**, quero **ver a agenda de todos os veterinários num dia**, para **acompanhar a ocupação da clínica**. | S1 | Could | P | Por escrever (E2) |
| 19 | H19 | EP4 | Como **veterinário**, quero **registar uma vacina com a data da próxima dose**, para **saber quando o animal deve voltar**. | S2, S5 | Could | P | Por escrever (E2) |

**Totais:** 9 histórias *Must* (5 M e 4 P), o objetivo do sprint 1 · 6 *Should*, que entram no sprint 1 pela ordem acima se houver capacidade · 4 *Could*.

H16 está como *Could*, mas **pode subir a Must** se, no E2, a regra das urgências escolhida for "blocos reservados" (ver R08 e conflito C1).

### 4.1 Won't (não desta vez)

Ficam registadas para que a IA, e o grupo, não as voltem a propor. Correspondem à lista "fora do âmbito" da [visão](visao.md#62-fora-do-âmbito).

| ID | História | Porquê |
|----|----------|--------|
| W1 | Como **tutor**, quero **receber um lembrete por SMS ou email** antes da consulta. | Serviços externos e contactos reais. |
| W2 | Como **tutor**, quero **marcar consultas num portal ou numa app**. | Outro canal para o mesmo caso de uso; exige autenticação de clientes. |
| W3 | Como **rececionista**, quero **emitir a fatura da consulta**. | Regras fiscais; fora da dificuldade do domínio. |
| W4 | Como **veterinário**, quero **passar uma receita eletrónica e dar baixa do stock**. | Outro domínio (farmácia e stock). |
| W5 | Como **utilizador**, quero **entrar com email e palavra-passe**. | A gestão de contas não é avaliada; H10 simplifica. |
| W6 | Como **veterinário**, quero **exportar o histórico do animal para PDF**. | Não resolve nenhum dos problemas P1 a P4. |

## 5. Critérios de aceitação

Escrevemos critérios para todas as histórias *Must*. As **três mais importantes**, uma por cada dificuldade do domínio indicada no enunciado (agenda por veterinário, urgências, histórico), são **H1**, **H6** e **H8**; foram escritas primeiro e com mais detalhe. As regras de negócio aparecem aqui como critérios testáveis, com valores concretos.

Valores usados nos exemplos (fictícios, a confirmar no E2): a clínica funciona de segunda a sábado, das 9h00 às 20h00; a consulta geral dura 30 minutos e a vacinação 20 minutos.

### H1 — Marcar consulta sem sobreposição · *uma das 3 mais importantes*

1. **Dado** que o veterinário A tem uma consulta das 10h00 às 10h30, **quando** a rececionista marca outra consulta geral com o veterinário A às 10h15, **então** o sistema recusa a marcação e indica a consulta em conflito.
2. **Dado** que o veterinário A tem uma consulta das 10h00 às 10h30, **quando** a rececionista marca uma consulta geral com o veterinário A às 10h30, **então** o sistema aceita (o intervalo é `[início, fim)`: começar quando a outra acaba não é sobreposição).
3. **Dado** que o veterinário A tem uma consulta das 10h00 às 10h30, **quando** a rececionista marca uma vacinação com o veterinário A às 10h05 (fica contida na outra), **então** o sistema recusa a marcação.
4. **Dado** que o veterinário A tem uma consulta das 10h00 às 10h30, **quando** a rececionista marca uma consulta geral com o veterinário B às 10h00, **então** o sistema aceita.
5. **Dado** um animal registado e um veterinário livre, **quando** a rececionista marca uma consulta geral às 11h00, **então** a consulta fica com fim às 11h30 (calculado pela duração do tipo) e no estado *Marcada*.

### H2 — Recusar marcações fora do horário ou no passado

1. **Dado** que a clínica fecha às 20h00, **quando** a rececionista marca uma consulta geral às 19h45, **então** o sistema recusa, porque a consulta acabaria às 20h15.
2. **Dado** que a clínica fecha às 20h00, **quando** a rececionista marca uma consulta geral às 19h30, **então** o sistema aceita (acaba exatamente às 20h00).
3. **Dado** que a clínica abre às 9h00 e não funciona ao domingo, **quando** a rececionista marca uma consulta às 8h50 ou num domingo, **então** o sistema recusa e explica porquê.
4. **Dado** que são 11h00 de hoje, **quando** a rececionista marca uma consulta para as 10h00 de hoje, **então** o sistema recusa, porque a hora já passou.

### H3 — Registar tutor e animal

1. **Dado** um tutor registado, **quando** a rececionista regista um animal com nome, espécie e esse tutor, **então** o animal fica associado ao tutor.
2. **Dado** o formulário de novo animal, **quando** a rececionista tenta guardar sem tutor, sem nome ou sem espécie, **então** o sistema recusa e indica o campo em falta.
3. **Dado** que já existe um animal com o microchip `900000000000001`, **quando** a rececionista regista outro animal com o mesmo microchip, **então** o sistema recusa.
4. **Dado** o formulário de novo animal, **quando** a rececionista indica um microchip com 14 ou 16 dígitos, **então** o sistema recusa (o microchip, se existir, tem exatamente 15 dígitos).

### H4 — Agenda diária do veterinário

1. **Dado** que o veterinário A tem consultas às 15h00, 9h30 e 11h00 de hoje e uma às 10h00 de amanhã, **quando** abre a agenda de hoje, **então** vê só as três de hoje, pela ordem 9h30, 11h00, 15h00.
2. **Dado** que o veterinário B tem uma consulta às 10h00 de hoje, **quando** o veterinário A abre a sua agenda de hoje, **então** essa consulta não aparece.

Fica para o E2 decidir se as consultas canceladas aparecem assinaladas ou ocultas.

### H5 — Registar chegada de urgência

1. **Dado** um animal registado, **quando** a rececionista regista a sua chegada como urgência, com o motivo, às 14h07, **então** a urgência fica no estado *Aguarda triagem*, com a hora de chegada 14h07 dada pelo relógio do sistema.
2. **Dado** um animal que ainda não está registado, **quando** a rececionista regista a urgência, **então** o sistema cria um registo mínimo do animal (nome, espécie, contacto do tutor) e a urgência fica na fila.

### H6 — Triagem · *uma das 3 mais importantes*

1. **Dado** que a urgência U1 (nível 2, chegada às 10h00) está na fila, **quando** o enfermeiro atribui o nível 1 à urgência U2 (chegada às 10h20), **então** a fila fica U2, U1 (o nível 1 é o mais grave e passa à frente).
2. **Dado** que U1 e U2 têm ambas o nível 2, com chegada às 10h00 e às 10h20, **quando** a fila é mostrada, **então** a ordem é U1, U2 (no mesmo nível, primeiro quem chegou primeiro).
3. **Dado** uma urgência no estado *Aguarda triagem*, **quando** um utilizador com perfil de rececionista tenta atribuir o nível, **então** o sistema recusa: só enfermeiros e veterinários fazem triagem (conflito C3).
4. **Dado** uma urgência, **quando** o enfermeiro tenta atribuir um nível que não seja 1, 2 ou 3, **então** o sistema recusa.

### H7 — Atender urgência

1. **Dado** a fila U2 (nível 1), U1 (nível 2), **quando** o veterinário A escolhe "atender a próxima", **então** U2 passa a *Em atendimento* com o veterinário A e sai da fila.
2. **Dado** que a fila está vazia, **quando** o veterinário escolhe "atender a próxima", **então** o sistema indica que não há urgências à espera.

O efeito de uma urgência nas consultas já marcadas depende da regra de encaixe, que só fica fechada no E2 (R08). Até lá, H7 não cumpre a Definition of Ready e não entra num sprint de construção.

### H8 — Nota clínica · *uma das 3 mais importantes*

1. **Dado** uma consulta *Em curso* com o veterinário A, **quando** A regista o motivo, as observações, o diagnóstico e o tratamento, **então** a nota fica *aberta* e associada à consulta e ao animal.
2. **Dado** uma nota aberta criada pelo veterinário A, **quando** A a altera, **então** a alteração é guardada; **quando** o veterinário B a tenta alterar, **então** o sistema recusa.
3. **Dado** uma nota aberta sem diagnóstico, **quando** o veterinário a tenta fechar, **então** o sistema recusa e indica o campo em falta.
4. **Dado** uma nota aberta completa, **quando** o veterinário a fecha, **então** a nota passa a *fechada*, com autor e data de fecho, e a consulta passa a *Concluída*.
5. **Dado** uma nota fechada, **quando** qualquer utilizador a tenta alterar ou apagar, **então** o sistema recusa e indica que as correções se fazem por adenda (H12).

### H9 — Histórico do animal

1. **Dado** um animal com uma consulta a 03/02, uma urgência a 10/05 e uma consulta a 20/09, **quando** o veterinário abre o histórico, **então** vê os registos pela ordem 20/09, 10/05, 03/02 (o mais recente primeiro), cada um com a data, o veterinário e o tipo.
2. **Dado** um animal com a alergia "penicilina" registada, **quando** o veterinário abre o histórico, **então** a alergia aparece no topo, antes de qualquer registo, sem ter de fazer scroll.
3. **Dado** uma nota fechada com uma adenda, **quando** o veterinário abre o histórico, **então** vê o texto original da nota e a adenda, com o autor e a data de cada um.

## 6. Verificação INVEST

Cada história do topo foi confrontada com o INVEST antes de entrar no backlog:

| Letra | O que verificámos | O que mudou por causa disso |
|:-----:|-------------------|-----------------------------|
| **I** Independente | Cada *Must* pode ser testada sozinha, com dados de demonstração (T02) a fazer de pré-condição. | H2 foi separada de H1 para se testar sem depender da regra da sobreposição. |
| **N** Negociável | As histórias dizem o quê e para quê, não como (nenhuma fala de ecrãs, tabelas ou tecnologia). | Os pormenores (canceladas na agenda, regra de encaixe) ficam para o E2. |
| **V** Valiosa | Cada história tem um stakeholder da análise e um benefício para ele. | Histórias técnicas ("Como sistema, quero uma base de dados…") não entram como histórias: ficam como itens técnicos (secção 7). |
| **E** Estimável | Todas têm tamanho P ou M. | — |
| **S** Pequena | Nenhuma é G. | A antiga "marcar consulta" (G) foi partida em H1 e H2. |
| **T** Testável | As *Must* têm critérios Dado/quando/então com valores concretos; nenhum critério diz "rápido" ou "fácil". | H7 está marcada como não pronta até a regra de encaixe estar fechada. |

## 7. Itens técnicos

Não são histórias de utilizador (não têm um stakeholder que os peça), mas o Scrum permite requisitos técnicos no backlog e entram no planeamento:

| ID | Item | Quando | Ligação |
|----|------|--------|---------|
| T01 | Projeto base .NET com projeto de testes, a compilar e a correr na integração contínua (GitHub Actions) | Sprint 1, primeiros dias (E3: repositório pronto a receber código) | R02, R09 |
| T02 | Ficheiro de dados de demonstração fictícios (tutores, animais, veterinários, horários), revisto pelo grupo | Início do sprint 1 | R03 |
| T03 | Ficheiro de contexto para a IA (stack, versões, regras: `TimeProvider`, pacotes permitidos, exclusões de âmbito) | Fecho do E3 | R02, R05, R07 |
| T04 | Modelo de pull request com a checklist da [Definition of Done](dod.md) | Fecho do E3 | R04, R06, R12 |

## 8. Candidatos aos 3 a 5 casos de uso a implementar

A seleção final é feita no E2. A proposta inicial cobre as três dificuldades do domínio (agenda por veterinário, urgências e histórico):

| Caso de uso | Histórias | Dificuldade do domínio coberta |
|-------------|-----------|--------------------------------|
| UC1 Marcar consulta | H1, H2, H4 | Agenda por veterinário |
| UC2 Gerir urgência | H5, H6, H7 | Urgências |
| UC3 Registar consulta | H8 | Histórico (escrita) |
| UC4 Consultar histórico do animal | H9 | Histórico (leitura) |
| UC5 Registar tutor e animal | H3 | Pré-condição dos restantes |

Se o tempo apertar, o UC5 pode ficar reduzido aos dados de demonstração (T02), mantendo os quatro casos de uso que cobrem as dificuldades do domínio.

## 9. Manutenção do backlog

- O PO reordena o backlog no Sprint Planning, com base no feedback do docente na Sprint Review e no registo de riscos.
- Uma história proposta pela IA só entra se o PO a aceitar e se tiver um stakeholder da análise. Se for rejeitada, fica registada, com a razão, na secção de requisitos rejeitados do E2.
- Na defesa, cada elemento tem de saber explicar porque é que cada história está no backlog e naquela posição: a secção 2 e a coluna Stakeholder servem para isso.
- Quando chegar o pedido de mudança, entra como história nova no topo do sprint 2, com análise de impacto feita a partir da matriz de rastreabilidade.
