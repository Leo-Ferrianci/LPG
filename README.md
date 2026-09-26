# Project LPG — Personal Operating System (POS)

Sistema de produtividade pessoal gamificada que centraliza **tarefas, hábitos, finanças e rotina de treinos** em um único ecossistema, com painel unificado e análise financeira assistida por inteligência artificial.

> Trabalho acadêmico — documentação do *Personal Operating System* (POS) desenvolvido no **Project LPG**.  
> Aplicação disponível na web e no Android (Google Play).

---

## 1. Título e descrição do sistema

O **Project LPG** (*Life Productivity Gamified*) é concebido como um **Sistema Operacional Pessoal (POS)**: uma camada única em que o usuário registra, organiza e acompanha a vida prática — o que precisa fazer, o que costuma repetir, o que gasta ou recebe, e como treina — sem espalhar essas informações em dezenas de aplicativos.

A analogia com um sistema operacional é intencional. Assim como o SO do computador concentra arquivos, processos e notificações, o POS concentra:

| Camada | Função no LPG |
|--------|----------------|
| **Execução** | Missões/tarefas, cronômetro de foco (Pomodoro) e lembretes |
| **Rotina** | Hábitos, streaks e registro de treinos |
| **Recursos** | Entradas e saídas financeiras, categorias, bancos e exportação |
| **Feedback** | Painel inicial (XP, conclusões, progresso) e relatórios via IA |

A proposta não é “mais um app de lista”. É **reduzir a fragmentação** da gestão pessoal e transformar dados do dia a dia em **decisão** — principalmente no módulo financeiro, por meio da exportação estruturada (`.csv`) e da análise com um assistente de IA (Gemini).

**Acesso**

| Canal | Endereço |
|-------|----------|
| Web / PWA | [https://projectlpg.com](https://projectlpg.com) |
| Google Play | [Project LPG na Play Store](https://play.google.com/store/apps/details?id=com.projectlpg.app) |

---

## 2. Desafios e diagnóstico

### 2.1 Rotina fragmentada

O diagnóstico de partida é comum na vida acadêmica e profissional:

- Tarefas ficam no bloco de notas, no WhatsApp ou na memória.
- Gastos ficam no extrato do banco, sem categoria nem visão do mês.
- Hábitos e treinos são “combinados consigo mesmo” e somem na primeira semana cheia.
- Cada ferramenta resolve **um** pedaço e nenhuma responde: *como está a minha semana como um todo?*

Essa fragmentação gera três custos reais:

1. **Custo cognitivo** — lembrar *onde* está cada informação.
2. **Custo de tempo** — abrir vários apps para uma decisão simples (posso gastar isso? o que vence hoje?).
3. **Custo emocional** — sensação de atraso permanente, mesmo quando parte da rotina está em dia.

### 2.2 Desafios de produtividade e gestão do tempo

| Desafio observado | Como aparece no cotidiano | Como o POS ataca |
|-------------------|---------------------------|------------------|
| Procrastinação | Começar sem recorte de tempo | Modo foco com ciclos de concentração e pausa (Pomodoro) |
| Falta de captura | Ideias e contas “depois eu anoto” | Tarefas, lembretes e lançamentos no mesmo app |
| Finanças invisíveis | Só se vê o saldo depois do gasto | Registro + CSV + análise por IA |
| Rotina que não se vê | Treino e hábito sem histórico | Hábitos, logs e módulo de exercício |
| Sobrecarga mental | Várias listas, nenhum painel | Dashboard unificado (início, XP, conclusões) |

O projeto parte desse diagnóstico: **produtividade pessoal falha menos por falta de vontade e mais por falta de um sistema único e visível.**

---

## 3. Métodos e ferramentas utilizadas

### 3.1 Métodos de produtividade aplicados

O LPG não é um “clone” de um único método. Ele **embute práticas consolidadas** no fluxo do app:

| Método | Aplicação no Project LPG |
|--------|---------------------------|
| **Pomodoro** | Modo foco nas tarefas: blocos de concentração, pausa e cronômetro persistente (o ciclo fica salvo, não some ao atualizar a página). |
| **GTD (Getting Things Done)** | Captura em listas (missões/tarefas e lembretes), revisão no painel e execução com data — “tirar da cabeça e pôr num sistema confiável”. |
| **Priorização (espírito Eisenhower / urgência × importância)** | Separação entre o que é do dia (tarefas ativas, vencimentos, hábitos) e o que é de médio prazo (objetivos, progresso). O usuário vê o que vence *agora* sem misturar com o estoque de ideias. |
| **Gamificação** | XP, conclusões e feedback visual para reforçar consistência, sem substituir o registro real das ações. |

### 3.2 Módulos do sistema

| Módulo | O que o usuário faz | Resultado |
|--------|---------------------|-----------|
| **Tarefas (missões)** | Cria, organiza, cronometra e conclui atividades; usa calendário e lembretes | Gestão do tempo no estilo lista + agenda (próximo de um board pessoal) |
| **Hábitos** | Marca o dia, acompanha sequência, registra falha de forma consciente | Rotina visível, menos “tudo ou nada” |
| **Financeiro** | Lança entradas e saídas (a receber / a pagar), categorias, bancos, importação de extrato e **exportação CSV** | Base para decisão orçamentária |
| **Treino / corpo** | Registro de exercícios e acompanhamento da rotina física | Saúde e consistência no mesmo POS |
| **Painel (Início)** | Vê objetivos, conclusões, XP e o que está ativo | Dashboard unificado da rubrica acadêmica |

### 3.3 Stack (visão de arquitetura)

| Camada | Tecnologia |
|--------|------------|
| Interface (web e app) | React, TypeScript, Vite, PWA; app Android (Capacitor) |
| API | AdonisJS, PostgreSQL, autenticação por sessão (e-mail ou Google) |
| Inteligência (híbrida) | Exportação CSV no app + análise no Gemini (fora do núcleo transacional) |

A escolha da IA **híbrida** (dados no app, análise no modelo) atende ao requisito de IA da disciplina **e** preserva o controle do usuário sobre o que sai do sistema.

---

## 4. Integração com inteligência artificial

### 4.1 Por que híbrida?

Uma IA “dentro” de cada clique aumentaria custo, privacidade e complexidade. O LPG adota um fluxo **explícito e auditável**:

1. O sistema **já possui** os dados financeiros estruturados (data, tipo, valor, descrição, categoria, banco, método, recorrência).
2. O usuário **exporta** um arquivo `.csv` (nada é apagado no app).
3. Esse arquivo é enviado a um **assistente de IA especializado** (Gemini).
4. A IA devolve um **relatório executivo**: padrões de gasto, gargalos, comparativo entrada × saída e recomendações.

Isso caracteriza IA aplicada à **tomada de decisão**, não apenas um chatbot genérico.

### 4.2 O que o CSV contém

| Campo | Significado para a análise |
|-------|----------------------------|
| `data` | Linha do tempo e sazonalidade |
| `tipo` | `entrada` (a receber / ganho) ou `saida` (a pagar / gasto) |
| `valor` | Magnitude do lançamento |
| `descricao` | Contexto (aluguel, mercado, freelance…) |
| `categoria` | Agrupamento para achar onde o orçamento vaza |
| `banco` | Origem/destino do dinheiro |
| `metodo` | Pix, débito, crédito etc. |
| `fixo` | Distingue recorrente de pontual |

### 4.3 Exemplo de uso acadêmico / profissional

No Gemini (ou agente equivalente), o aluno anexa o CSV e pode pedir, por exemplo:

> Analise este extrato do Project LPG. Resuma receitas versus despesas no período, indique as três categorias que mais pesam, aponte meses atípicos e sugira três ajustes práticos de orçamento, sem inventar valores que não estejam no arquivo.

A IA **resume, organiza e recomenda**; o POS **continua sendo a fonte da verdade**.

---

## 5. Fluxo de organização

```
                    ┌─────────────────────────┐
                    │   Project LPG (POS)     │
                    │  Web / Android / PWA    │
                    └───────────┬─────────────┘
                                │
        ┌───────────┬───────────┼───────────┬───────────┐
        ▼           ▼           ▼           ▼           ▼
   Tarefas      Hábitos     Financeiro    Treinos    Painel
   + Foco       + streak    + importar    + logs     XP /
   Pomodoro                 + exportar               objetivos
                                │
                                ▼
                         arquivo .csv
                                │
                                ▼
                    Assistente IA (Gemini)
                                │
                                ▼
              Relatório: insights + recomendações
```

**Passo a passo (uso típico da semana)**

1. **Capturar** — anotar missão, hábito ou lançamento no mesmo dia (GTD).
2. **Executar** — usar o modo foco (Pomodoro) na tarefa da vez.
3. **Revisar** — olhar o Início: o que fechou, o que venceu, o XP do período.
4. **Medir o dinheiro** — lançar ou importar extrato; exportar o CSV quando for hora de decidir (corte de gasto, meta de poupança, fechamento do mês).
5. **Decidir com IA** — enviar o CSV ao Gemini e voltar ao POS só com as ações escolhidas (não com mais uma planilha paralela).

---

## 6. Guia de utilização e acesso

### 6.1 Links oficiais

| Recurso | URL |
|---------|-----|
| Aplicação web | [https://projectlpg.com](https://projectlpg.com) |
| Android (Play Store) | [https://play.google.com/store/apps/details?id=com.projectlpg.app](https://play.google.com/store/apps/details?id=com.projectlpg.app) |
| Planos (web) | [https://projectlpg.com/planos](https://projectlpg.com/planos) |
| Privacidade | [https://projectlpg.com/privacidade](https://projectlpg.com/privacidade) |

### 6.2 Como começar (demonstração)

1. Acesse a web ou instale o app na Play Store.  
2. Crie conta (e-mail e senha) ou entre com Google.  
3. No **Início**, veja o painel (objetivos e progresso).  
4. Em **Tarefas / Missões**, crie um item e, se quiser, inicie o **foco** (Pomodoro).  
5. Em **Hábitos**, marque o dia; em **Saúde / treino**, registre o exercício.  
6. Em **Dinheiro**, lance entradas e saídas (ou importe extrato).  
7. Clique em **Exportar** (ao lado de Importar) e baixe o `lpg-financeiro-AAAA-MM-DD.csv`.  
8. Envie o arquivo ao Gemini com um pedido de relatório executivo.

### 6.3 Observação para a banca

O núcleo do POS roda no próprio produto. A etapa de IA é **deliberadamente externa** (CSV → Gemini), o que facilita demonstrar em sala: abre-se o app, exporta-se o arquivo e mostra-se o relatório gerado na hora.

---

## 7. Principais ganhos — produtividade e saúde mental

| Dimensão | Ganho |
|----------|--------|
| **Gestão do tempo** | Um lugar para o que é urgente (hoje) e para o que é importante (hábitos, objetivos). |
| **Menos procrastinação** | Começar fica menor: um ciclo de foco, não “a tarefa inteira da vida”. |
| **Menos carga mental** | Menos abas, menos “onde eu anotei isso?”. |
| **Dinheiro consciente** | Ver categoria e tendência, em vez de só o susto no fim do mês. |
| **Decisão assistida** | A IA traduz a planilha em linguagem de ação, sem o usuário precisar ser analista. |
| **Corpo e rotina** | Treino e hábito no mesmo sistema em que estão as missões — a saúde deixa de ser “outro app que eu abandono”. |
| **Comunicação** | Objetivos e tarefas visíveis (inclusive em contextos de grupo/empresa no produto) reduzem combinados soltos só no chat. |

Em síntese, o Project LPG trata produtividade como **sistema + hábito + dado**, e a IA como **lente** sobre o dado financeiro — alinhado à rubrica: diagnóstico, métodos clássicos, painel digital, IA para decisão, e cuidado com sobrecarga e saúde mental.

---

## 8. Relação com a rubrica da disciplina

| Requisito | Onde o projeto atende |
|-----------|------------------------|
| 1. Diagnóstico da rotina e desafios reais | Seção 2 — fragmentação, procrastinação, finanças invisíveis |
| 2. Métodos consolidados | Seção 3.1 — Pomodoro, GTD, priorização, gamificação |
| 3. Ferramentas digitais e dashboard | Web, Android, painel Início e módulos integrados |
| 4. IA para organizar / decidir | Seção 4 — CSV + Gemini (relatório executivo) |
| 5. Comunicação, procrastinação e saúde mental | Foco em ciclos, um só sistema, hábitos/treino, menos ruído cognitivo |

---

**Project LPG** — *Personal Operating System*  
Documentação acadêmica do produto. Repositório de apresentação; o desenvolvimento do sistema vive no monorepo da aplicação.
