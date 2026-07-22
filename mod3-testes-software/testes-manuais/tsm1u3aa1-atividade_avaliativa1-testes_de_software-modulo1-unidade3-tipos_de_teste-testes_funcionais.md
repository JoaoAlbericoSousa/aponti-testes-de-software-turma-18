### **TsM1U3AA1- Atividade Avaliativa 1 - Testes de Software - Módulo 1 - Unidade 3 - Tipos de teste - TESTES FUNCIONAIS**


## 1. Análise de Sistema  (SGP)
Dado um sistema fictício, os alunos deverão analisar suas funcionalidades e indicar:

*   Quais testes seriam **unitários**
*   Quais testes seriam de **integração**
*   Quais testes seriam de **sistema**
*   Quais testes seriam de **aceitação**

### 1.2. Justificação
Justificar as escolhas com base no **objetivo** e no **nível** do teste.

## 1.3. Sistema Fictício - Sistema de Gerenciamento de Pedidos (SGP) 
O SGP é uma aplicação web utilizada por clientes e administradores para realizar e gerenciar pedidos de produtos online.


| **INTEGRAÇÕES**  | **FUNCIONALIDADES PRINCIPAIS**  | **REGRAS DE NEGÓCIO**  |
| :--- | :--- | :--- |
| Integração com banco de dados de produtos | Cadastro e autenticação de usuários | O pedido deve conter pelo menos um item |
| Integração com serviço de autenticação | Consulta de produtos disponíveis| O valor total deve considerar quantidade e preço dos produtos |
| Integração com serviço de pedidos | Adição e remoção de itens no carrinho | Usuários não autenticados não podem finalizar pedidos |
| Ø | Cálculo automático do valor total do pedido | Após a confirmação, o pedido não pode ser alterado |
| Ø | Finalização do pedido com confirmação | Ø |

---

# 📑 Análise de Testes: Sistema de Gerenciamento de Pedidos (SGP)

Este documento divide os testes do SGP nos quatro níveis fundamentais da engenharia de software, justificando cada escolha com base em seu objetivo específico.

---

## 1.** TESTES UNITÁRIOS** (Componentes atômicos - funções, métodos e classes)

### 🧪 O que seria testado neste nível:
*   **Função de Cálculo do Total:** Testar isoladamente a função matemática que multiplica `quantidade × preço` de um produto.
*   **Validação do Carrinho Vazio:** Testar o método responsável por verificar se a lista de itens do pedido está maior que zero antes de permitir o avanço.
*   **Componente de Interface (Botão "Adicionar"):** Testar se a função do botão do carrinho é disparada corretamente ao ser clicada.

### 💡 Justificativa:
*   **Objetivo:** Verificar se a menor unidade de código (funções, métodos ou classes) funciona corretamente de forma isolada.
*   **Nível:** Mais baixo/atômico. Não há comunicação com banco de dados ou APIs externas aqui; usa-se *mocks* (simuladores) para garantir o isolamento do código puro.

---

## 2. **TESTES DE INTEGRAÇÃO** (Módulos, componentes ou serviços)

### 🧪 O que seria testado neste nível:
*   **Fluxo de Login (SGP ↔ Serviço de Autenticação):** Testar se os dados digitados na tela do SGP são enviados e validados corretamente pelo serviço externo de autenticação.
*   **Persistência no Banco (SGP ↔ Banco de Dados):** Testar se a consulta de produtos realmente busca os dados corretos nas tabelas do banco de dados.
*   **Comunicação de Pedidos (SGP ↔ Serviço de Pedidos):** Testar se a API do serviço de pedidos recebe o payload correto após o fechamento do carrinho.

### 💡 Justificativa:
*   **Objetivo:** Validar se a comunicação, as interfaces e a troca de dados entre dois ou mais módulos/sistemas funcionam perfeitamente.
*   **Nível:** Intermediário. Foca nos pontos de contato e nos contratos de comunicação entre os sistemas que compõem o ecossistema do SGP.

---

## 3. **TESTES DE SISTEMA** (Testa o sistema completo em um ambiente controlado )

### 🧪 O que seria testado neste nível:
*   **Fluxo de Bloqueio (Regra de Negócio):** Tentar finalizar um pedido sem estar autenticado e garantir que o sistema exiba a mensagem correta e bloqueie a ação.
*   **Fluxo Ponta a Ponta do Cliente:** Entrar no site ➔ Buscar produto ➔ Adicionar ao carrinho ➔ Autenticar ➔ Finalizar pedido com sucesso.
*   **Imutabilidade do Pedido:** Tentar alterar a quantidade de um item ou excluir um produto logo após receber a tela de confirmação do pedido (deve ser bloqueado).

### 💡 Justificativa:
*   **Objetivo:** Avaliar o comportamento do sistema como um todo, garantindo que todas as regras de negócio e funcionalidades principais operem em harmonia no ambiente completo.
*   **Nível:** Alto. O sistema é testado de forma integrada e completa, simulando o comportamento real esperado para o software em execução.

---

## 4. **TESTES DE ACEITAÇÃO** (Se o sistema atende às necessidades do negócio e do usuário final)

### 🧪 O que seria testado neste nível:
*   **Jornada de Compra do Usuário (UAT ¹):** Um cliente real ou a equipe de produto realiza compras para validar se o fluxo é intuitivo, rápido e atende às expectativas de mercado.
*   **Validação Regulatória/Contratual:** Garantir que o processo de autenticação e armazenamento de dados de pedidos está em conformidade com leis de privacidade (como a LGPD).

### 💡 Justificativa:
*   **Objetivo:** Validar se o sistema atende aos requisitos de negócio iniciais e se está pronto para ser implantado em produção para os usuários finais.
*   **Nível:** Mais alto/Critério de Pronto. Foca na perspectiva do cliente e no valor de negócio entregue, validando o software contra o que foi planejado comercialmente.

---

## [ ¹ ] O que é UAT?

UAT significa User Acceptance Testing (que em português é traduzido como Teste de Aceitação do Usuário).
É a fase final do processo de testes de software, realizada antes que o sistema seja lançado oficialmente (em produção) para o público geral.

### Como funciona na prática?

*   **O objetivo:** Não é encontrar pequenos bugs técnicos, mas sim validar se o software atende às necessidades reais do negócio e se funciona corretamente na perspectiva de quem vai utilizá-lo no dia a dia.
*   **Quem executa:** O teste é feito pelos próprios usuários finais (ou por representantes da área de negócio do cliente), e não pelos desenvolvedores ou analistas de QA.
*   **Cenário:** É executado em um ambiente de homologação, utilizando dados e situações que simulam o mundo real.

### Por que ele é tão importante?

1. **Garantia de valor:** Um software pode estar tecnicamente perfeito (sem falhas de código), mas se for difícil de usar ou não resolver o problema da empresa, ele falhará no mercado. O UAT evita isso.
2. **Aprovação oficial (Sign-off):** É a etapa onde o cliente dá o "sinal verde" de que a entrega foi satisfatória e está pronta para o "go-live" (quando o projeto sai do ambiente de testes e entra em produção).
