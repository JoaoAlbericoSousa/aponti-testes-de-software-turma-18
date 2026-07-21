# :memo: Atividade Avaliativa - Módulo 02 - Aula 02 - Ciclo de Vida dos Testes

1. Produzir uma tabela comparativa entre metodologia Ágil e em Cascata.
2. Indicar como os testes acontecem em cada modelo e as Vantagens x Limitações.

## 📊 TABELA COMPARATIVA EM METODOLOGIA ÁGIL OU EM CASCATA

| **Critério / Metodologia** | **ÁGIL** | **CASCATA** |
| :--- | :--- | :--- |
| **Abordagem Geral** | Iterativa e incremental (ciclos/sprints). | Linear e sequencial (etapas fixas). |
| **Definição de Requisitos** | Evolutivos e abertos a mudanças. | Fixos e definidos no início do projeto. |
| **Vantagens** | Feedback rápido, alta adaptabilidade e valor entregue cedo. | Alta previsibilidade de prazos, custos e escopo claro. |
| **Desvantagens** | Falta de previsibilidade (difícil prever o custo final e o prazo de entrega de um projeto complexo logo ), Documentação insuficiente (o foco na entrega pode dificultar a manutenção futura) | Difícil adaptação a mudanças e Etapas rígidas|
| **Limitações** | Escopo imprevisível e exige alta dedicação do cliente. | Difícil de alterar e riscos descobertos tarde demais. |
| **Como Ocorrem os Testes** | Contínuos; realizados em paralelo ao desenvolvimento a cada sprint. | Tardios; executados apenas em uma fase específica após o fim do desenvolvimento. |

---

# 📋 Análise: Ciclo de Vida de Testes (Cascata vs. Ágil)

O documento apresenta uma análise comparativa de como o teste de software e o seu ciclo de vida (STLC) se integram nos modelos Cascata (Waterfall) e Ágil, destacando o funcionamento, as vantagens e as limitações de cada abordagem.

---

## 🌊 Modelo em Cascata (Waterfall)

O modelo em Cascata é uma abordagem sequencial e linear, onde o desenvolvimento do software avança de forma rígida através de fases bem definidas.

### ⚙️ Como os testes acontecem
* **Fase tardia**: Os testes ocorrem em uma fase exclusiva, localizada quase no final do ciclo de desenvolvimento.
* **Dependência de código**: A execução dos testes exige que todo o código e as funcionalidades estejam 100% concluídos.
* **Documentação rigorosa**: O ciclo de testes baseia-se fortemente em especificações de requisitos e planos de testes estáticos pré-aprovados.
* **Processo formal**: Segue a sequência estrita de planeamento, especificação, execução, registo de defeitos e encerramento.

### ⚖️ Vantagens x Limitações

#### 🟢 Vantagens
* **Clareza estrutural**: Fases, prazos e entregáveis de testes são claramente definidos desde o início.
* **Documentação robusta**: Casos de teste detalhados facilitam a auditoria e o entendimento futuro do sistema.
* **Facilidade de gestão**: Ideal para projetos com requisitos estáveis que não vão sofrer alterações.

#### 🔴 Limitações
* **Deteção tardia de falhas**: Os bugs são encontrados no final do projeto, tornando as correções complexas e dispendiosas.
* **Alto risco de atrasos**: Qualquer atraso no desenvolvimento reduz diretamente o tempo disponível para a equipa de testes.
* **Inflexibilidade**: Alterações nos requisitos durante a fase de testes exigem o reinício de todo o ciclo do projeto.

---

## 🏃 Modelo Ágil (Agile)

O modelo Ágil baseia-se no desenvolvimento iterativo e incremental, onde o software é construído em ciclos curtos denominados *Sprints*.

### ⚙️ Como os testes acontecem
* **Abordagem contínua**: Os testes ocorrem em paralelo com o desenvolvimento desde o primeiro dia de cada iteração.
* **Testes precoces (Shift-Left)**: A equipa de QA valida os requisitos (User Stories) antes mesmo de o código ser escrito.
* **Colaboração direta**: Engenheiros de testes, programadores e a área de negócio trabalham juntos diariamente.
* **Automação essencial**: Utilização frequente de automação de testes (regressão) para garantir o ritmo das entregas rápidas.

### ⚖️ Vantagens x Limitações

#### 🟢 Vantagens
* **Feedback rápido**: Defeitos são identificados e corrigidos quase em tempo real, reduzindo o custo técnico.
* **Alta adaptabilidade**: O plano de testes molda-se facilmente às mudanças de prioridades do negócio.
* **Qualidade partilhada**: A responsabilidade pela qualidade do software passa a ser de toda a equipa e não apenas dos testadores.

#### 🔴 Limitações
* **Documentação reduzida**: O foco em software funcional pode resultar em casos de teste menos detalhados e menor rastreabilidade histórica.
* **Pressão por tempo**: O curto espaço de tempo das *Sprints* pode comprometer a profundidade de testes mais complexos.
* **Falta de visão global**: O foco em pequenas partes pode fazer com que falhas de integração sistémica passem despercebidas temporariamente.

---

## 📊 Tabela Comparativa Resumida

| Critério | Modelo em Cascata | Modelo Ágil |
| :--- | :--- | :--- |
| **Início dos Testes** | Final do desenvolvimento | Início do projeto (contínuo) |
| **Foco Principal** | Conformidade com o plano inicial | Satisfação do cliente e valor rápido |
| **Custo de Mudança** | Muito elevado | Baixo e expectável |
| **Automação** | Opcional / Secundária | Crítica e mandatória |
