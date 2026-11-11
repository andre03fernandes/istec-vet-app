# Visão do sistema

> E1 · Parte 1 — problema, utilizadores e âmbito.
> Todos os nomes de organizações e pessoas neste documento são fictícios.

## 1. Contexto

A **Clínica Veterinária Quatro Patas** (fictícia) é uma clínica de animais de companhia, de dimensão média, numa zona urbana:

- 3 médicos veterinários, 2 enfermeiros veterinários, 2 rececionistas e uma diretora clínica, que também dá consultas;
- 2 consultórios e 1 sala de tratamentos;
- funciona de segunda a sábado, das 9h00 às 20h00;
- faz cerca de 35 consultas programadas por dia e recebe, em média, 3 a 5 urgências por dia, sem aviso prévio.

Hoje a agenda é uma folha de cálculo partilhada, mais uma agenda em papel na receção. A ficha clínica de cada animal está dividida entre fichas em papel e notas soltas no computador de cada veterinário.

## 2. Problema

| # | Problema | Quem o sente | Consequência hoje |
|---|----------|--------------|-------------------|
| P1 | **Marcações sobrepostas.** Duas rececionistas marcam ao mesmo tempo, na folha de cálculo e no papel, para o mesmo veterinário e à mesma hora. | Rececionistas, veterinários, tutores | Tutores à espera, consultas encurtadas, reclamações. |
| P2 | **As urgências desorganizam a agenda.** Quando entra uma urgência, ninguém sabe que veterinário está livre nem que consultas vão atrasar. A decisão é tomada de cabeça, ao balcão. | Rececionistas, veterinários | Animais graves esperam mais do que deviam; os tutores das consultas seguintes não são avisados. |
| P3 | **Histórico clínico disperso.** O veterinário de serviço não vê o que outro colega registou (alergias, medicação, cirurgias anteriores). | Veterinários, enfermeiros | Perguntas repetidas ao tutor, risco de prescrever um fármaco a que o animal é alérgico. |
| P4 | **Não se sabe quem alterou o quê.** Os registos clínicos em papel e na folha de cálculo podem ser corrigidos sem rasto. | Diretora clínica | Fragilidade perante uma reclamação ou uma inspeção. |

**Declaração do problema.** O problema da *agenda partilhada sem controlo de conflitos e do histórico clínico disperso* afeta *rececionistas, veterinários e, indiretamente, os tutores*. O impacto é *marcações sobrepostas, urgências mal encaixadas e decisões clínicas tomadas sem o histórico completo do animal*. Uma solução bem-sucedida *impede marcações sobrepostas por veterinário, encaixa as urgências por prioridade de triagem e mostra num só ecrã o histórico do animal, sem permitir apagar registos clínicos*.

## 3. Declaração de visão

> **Para** a receção e a equipa clínica de uma clínica veterinária de animais de companhia,
> **que** precisam de marcar consultas sem conflitos, encaixar urgências e consultar o histórico do animal,
> **o istec-vet-app** é um sistema de gestão de agenda e de ficha clínica
> **que** garante que nenhum veterinário tem duas consultas sobrepostas, ordena as urgências por prioridade de triagem e mantém um histórico clínico cronológico e não apagável.
> **Ao contrário** da folha de cálculo partilhada e das fichas em papel,
> **o nosso produto** valida cada marcação no momento em que é feita e guarda quem registou cada nota clínica e quando.

## 4. Objetivos (SMART)

Os valores são medidos sobre os dados fictícios de demonstração e sobre os testes automáticos do grupo.

| ID | Objetivo | Como se mede | Prazo |
|----|----------|--------------|-------|
| OB1 | O sistema recusa 100% das marcações que se sobrepõem a outra consulta do mesmo veterinário, incluindo os casos-limite (consulta que começa exatamente quando outra acaba, consulta que atravessa o fecho da clínica). | Casos de teste de valores-limite do E3 a passar | E4 (22/01/2027) |
| OB2 | Uma urgência registada aparece na fila de urgências ordenada por nível de triagem e, dentro do mesmo nível, por hora de chegada. | Casos de teste do caso de uso "Gerir urgência" (UC2) | E4 |
| OB3 | O histórico de um animal mostra todas as consultas, urgências e notas clínicas por ordem cronológica, num único ecrã. | Teste de aceitação com um animal de demonstração com ≥ 10 registos | E4 |
| OB4 | Nenhuma nota clínica fechada pode ser apagada ou alterada; as correções ficam como adenda, com autor e data. | Testes que tentam alterar e apagar uma nota fechada e esperam erro | E4 |
| OB5 | Implementar 3 a 5 casos de uso de ponta a ponta, todos cobertos por testes automáticos. | Matriz de rastreabilidade requisito → teste sem lacunas | E4 |

## 5. Utilizadores

### 5.1 Utilizadores diretos (usam o sistema)

| Perfil | O que faz no sistema | Frequência | O que mais lhe importa |
|--------|----------------------|------------|------------------------|
| **Rececionista** | Regista tutores e animais, marca, reagenda e cancela consultas, regista a chegada de urgências. | Todo o dia, dezenas de vezes | Marcar depressa, ao telefone, sem erros; ver de imediato que veterinário está livre. |
| **Médico veterinário** | Vê a sua agenda do dia, consulta o histórico do animal, regista a nota clínica da consulta, atende urgências. | Em cada consulta | Ver o histórico completo antes de entrar o animal; registar a consulta em pouco tempo. |
| **Enfermeiro veterinário** | Faz a triagem inicial das urgências (atribui o nível de prioridade) e consulta o histórico. | Em cada urgência | Classificar a urgência rapidamente e passá-la ao veterinário certo. |
| **Diretora clínica** | Define o horário de trabalho de cada veterinário; consulta a agenda de todos. | Semanal | Ocupação da agenda, rastreabilidade dos registos clínicos. |

### 5.2 Afetados, mas que não usam o sistema nesta versão

| Perfil | Como é afetado |
|--------|----------------|
| **Tutor do animal** | É quem pede a consulta (por telefone ou ao balcão). Beneficia de menos esperas e de um histórico do animal mais completo. Nesta versão não tem acesso ao sistema (ver fora do âmbito). |
| **Animal** | É a entidade central da ficha clínica. Não é utilizador, mas todas as regras de negócio existem para proteger a sua saúde. |

## 6. Âmbito

### 6.1 Dentro do âmbito

| Área | O que inclui |
|------|--------------|
| **Tutores e animais** | Registo do tutor (dados fictícios) e dos seus animais: nome, espécie, raça, data de nascimento, sexo, número de microchip (opcional), alergias conhecidas. |
| **Agenda por veterinário** | Horário de trabalho de cada veterinário; marcação, reagendamento e cancelamento de consultas, com validação de sobreposição; vista da agenda diária de cada veterinário. |
| **Urgências** | Registo da chegada de uma urgência com nível de triagem; fila de urgências ordenada por prioridade; atribuição a um veterinário. |
| **Ficha clínica e histórico** | Nota clínica de cada consulta ou urgência (motivo, observações, diagnóstico, tratamento); fecho da nota; adendas a notas fechadas; histórico cronológico do animal. |
| **Estados da consulta** | Marcada → em curso → concluída, ou cancelada / falta (entidade principal para o diagrama de estados do E3). |

Destas áreas saem os **3 a 5 casos de uso a implementar de ponta a ponta**. A escolha final é feita no E2, a partir do topo do [backlog](backlog.md).

### 6.2 Fora do âmbito

Fica explicitamente fora do âmbito, e serve de lista de exclusões a incluir nos prompts, para a IA não acrescentar funcionalidades que não pedimos:

| Fora do âmbito | Porquê |
|----------------|--------|
| Faturação, pagamentos e integração com software de contabilidade | Não faz parte da dificuldade do domínio (agenda, urgências, histórico) e implica regras fiscais. |
| Portal ou app para o tutor marcar consultas sozinho | Duplica o caso de uso de marcação com outro canal; obrigaria a autenticação de clientes externos. |
| Envio real de SMS ou email (lembretes, avisos de atraso) | Depende de serviços externos e de contactos reais. No máximo, o sistema mostra que um aviso *seria* enviado. |
| Gestão de stock, farmácia e receitas eletrónicas | Outro domínio, com regras próprias de medicamentos veterinários. |
| Integração com o registo nacional de identificação de animais de companhia | Serviço externo e real; o número de microchip é guardado apenas como texto. |
| Internamento, cirurgias com bloco operatório e gestão de salas | Aumenta muito a agenda (recursos além do veterinário) sem acrescentar um caso de uso novo. |
| Resultados de laboratório e imagiologia (anexos, integrações) | Exige armazenamento de ficheiros e integrações externas. |
| Várias clínicas ou filiais | A clínica é única nesta versão. |
| Autenticação real (palavras-passe, SSO) | O perfil do utilizador é escolhido num ecrã de entrada simplificado; a gestão de contas não é avaliada. |
| Telemedicina e videoconsultas | Fora do problema descrito. |

## 7. Restrições e pressupostos

**Restrições** (impostas, não se discutem):

- O código é gerado por ferramentas de IA; o grupo especifica, decide e verifica (enunciado do projeto).
- Os testes são desenhados pelo grupo, a partir dos requisitos, **antes** de o código ser gerado.
- Só dados fictícios no sistema e nos prompts; nenhuma chave de API ou palavra-passe no repositório.
- Documentação em Markdown em `docs/`; diagramas em Mermaid.
- Stack prevista: C# / .NET, com testes automáticos executáveis (a confirmar com ADR no E3).
- Calendário: E2 a 06/12, E3 a 10/01, pedido de mudança na aula de 21/01 (turma A), E4 a 22/01.

**Pressupostos** (a validar com o docente, que faz de cliente):

- Cada consulta tem uma duração fixa por tipo (por exemplo, 20 min para vacinação e 30 min para consulta geral). Os valores exatos ficam fechados no E2.
- Uma consulta é sempre com um único veterinário.
- A triagem das urgências usa uma escala de 3 níveis (por exemplo, emergente, urgente, pouco urgente). A escala e a regra para encaixar urgências na agenda são o principal ponto em aberto (ver risco R08 em [risks.md](risks.md)).

## 8. Glossário

| Termo | Significado neste projeto |
|-------|---------------------------|
| **Tutor** | Pessoa responsável pelo animal. Não é utilizador do sistema. |
| **Animal** | Animal de companhia com ficha na clínica; pertence a um tutor. |
| **Consulta** | Marcação de um animal com um veterinário, num intervalo `[início, fim)`. |
| **Agenda** | Conjunto das consultas de um veterinário, dentro do seu horário de trabalho. |
| **Sobreposição** | Duas consultas do mesmo veterinário cujos intervalos se intersetam. Uma consulta que começa exatamente quando outra acaba **não** é sobreposição. |
| **Urgência** | Atendimento sem marcação, com um nível de triagem. |
| **Nível de triagem** | Prioridade clínica da urgência, atribuída pelo enfermeiro ou veterinário. |
| **Nota clínica** | Registo de uma consulta ou urgência. Fica **aberta** enquanto é editada e **fechada** depois de concluída. |
| **Adenda** | Correção ou complemento acrescentado a uma nota fechada, com autor e data. Não substitui o texto original. |
| **Histórico** | Lista cronológica de todas as consultas, urgências, notas e adendas de um animal. |
