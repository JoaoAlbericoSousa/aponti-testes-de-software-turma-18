### **TsM1U3AA2 - Atividade Avaliativa 2 - Testes de Software - Módulo 1 - Unidade 3 - Tipos de teste - TESTES NÃO FUNCIONAIS**

# Checklist de Testes não Funcionais baseado no sistema fictício PACO (Plataforma de Agendamento de Consultas)

Dado um sistema proposto (Plataforma de agendamento de Consultas), elabore um checklist de testes não funcionais, cobrindo obrigatoriamente:

*   Performance
*   Segurança
*   Usabilidade
*   Compatibilidade

Cada item do checklist deve indicar o que será verificado e qual o risco associado.

---

## Sistema Fictício - Plataforma de Agendamento de Consultas

A Plataforma (PACO) é um sistema web que permite que usuários realizem o agendamento de consultas médicas de forma simples e segura, enquanto administradores gerenciam horários e atendimentos.

| Integrações | Regras de Negócio | Funcionalidades Principais |
| :--- | :--- | :--- |
| • Sistema acessado via navegador web<br>• Usuários podem acessar por desktop, tablet ou celular<br>• Uso simultâneo por múltiplos usuários durante horários de pico | • Usuários devem estar autenticados para agendar consultas<br>• Não é permitido agendar dois horários simultâneos para o mesmo usuário<br>• Cancelamentos só podem ocorrer até 24h antes da consulta<br>• Dados pessoais devem ser protegidos conforme boas práticas de segurança | • Cadastro e autenticação de usuários<br>• Consulta de especialidades e profissionais disponíveis<br>• Agendamento, cancelamento e visualização de consultas<br>• Notificações de confirmação de agendamento<br>• Área administrativa para gestão de horários |

---


# 🚧 Plano de Testes Não Funcionais: Análise Didática e Checklist (Plataforma PACO)

Este documento apresenta uma análise profunda, expositiva e pedagógica dos requisitos não funcionais para a **Plataforma de Agendamento de Consultas (PACO)**. O objetivo é compreender não apenas *o que* testar, mas *por que* testar, conectando a engenharia de software aos impactos reais de negócio.

---

## 1. Contexto do Sistema

A Plataforma de Agendamento de Consultas (PACO) é um sistema web responsivo que permite a pacientes marcar consultas e a administradores gerir horários em computadores, tablets ou telemóveis. Devido ao grande volume de acessos simultâneos, a aplicação exige alta estabilidade de infraestrutura para evitar quedas de serviço.

Operacionalmente, o sistema impõe regras rígidas: obriga à autenticação prévia dos utilizadores, impede o agendamento de horários duplicados para o mesmo paciente e limita os cancelamentos até 24 horas antes da consulta. Por manipular dados de saúde e informações pessoais sensíveis, toda a arquitetura cumpre rigorosas normas de segurança digital para garantir a privacidade dos dados armazenados e em trânsito.

---

## 2. Análise Expositiva e Justificada do Checklist

### 🚀 2.1. Performance
A performance determina a percepção de eficiência do sistema. Em plataformas de saúde, a estabilidade e a velocidade influenciam diretamente a confiança do paciente no serviço prestado.

#### PERF-01: Tempo de Resposta em Operações Críticas
*   **Justificativa Didática:** Quando um paciente busca um médico, o sistema realiza consultas complexas no banco de dados (filtrando especialidade, local, horários livres e convênios). Se o tempo de resposta passar de 3 segundos, o cérebro humano percebe a espera como tédio ou falha. 
*   **Análise do Teste:** Deve-se medir o *Time to First Byte* (TTFB) e o tempo total de renderização da listagem de médicos e da confirmação do agendamento sob condições normais de uso.
*   **Risco Associado:** **Alto.** O usuário pode acreditar que o sistema travou e clicar repetidamente no botão "Confirmar". Isso gera requisições duplicadas, gerando sobrecarga no servidor e agendamentos fantasmas no banco de dados.

#### PERF-02: Escalabilidade e Comportamento em Horários de Pico (Testes de Carga e Estresse)
*   **Justificativa Didática:** Sistemas de saúde possuem picos previsíveis de acesso (ex: início da manhã ou logo após a abertura de agendas mensais de médicos populares). O sistema precisa aguentar a "enxurrada" de acessos sem degradar a experiência.
*   **Análise do Teste:** Simulação de carga sintética (usando ferramentas como JMeter ou K6) aplicando volumes crescentes de usuários simultâneos realizando o fluxo completo (login, busca e agendamento) até o limite especificado e além dele (estresse).
*   **Risco Associado:** **Crítico.** Sem a elasticidade correta, o servidor web esgota seu *pool* de conexões. O sistema sai do ar apresentando erros como *502 Bad Gateway* ou *504 Gateway Timeout*, interrompendo o faturamento e impossibilitando o trabalho dos administradores da clínica.

#### PERF-03: Consumo e Vazamento de Recursos do Servidor (*Memory Leaks*)
*   **Justificativa Didática:** O código do sistema precisa gerenciar bem a memória do servidor. Se uma busca por especialidades aloca dados na memória e não os libera após o término da requisição, o servidor vai perdendo capacidade gradativamente.
*   **Análise do Teste:** Monitoramento da curva de uso de CPU e memória RAM do servidor durante um período prolongado de uso contínuo (Teste de Endurance/Soak Testing).
*   **Risco Associado:** **Médio.** Degradação lenta e contínua do sistema. A plataforma começa o dia rápida e termina a noite extremamente lenta, exigindo reinicializações constantes e manuais do servidor pela equipe de infraestrutura.

---

### 🔒 2.2. Segurança da Informação
A segurança em sistemas de saúde é uma obrigação legal e ética. Dados médicos pertencem à categoria de dados sensíveis e exigem proteção máxima.

#### SEG-01: Criptografia e Proteção de Dados em Trânsito e Repouso
*   **Justificativa Didática:** Os dados do paciente (nome, CPF, histórico de consultas) trafegam pela internet pública entre o navegador e o servidor. Se esses dados forem enviados em texto claro, qualquer intermediário na rede (como um Wi-Fi público) pode interceptá-los.
*   **Análise do Teste:** Inspeção de pacotes para garantir o uso estrito de HTTPS/TLS 1.3. Varredura no banco de dados para confirmar que campos de identificação pessoal e senhas estejam criptografados (usando algoritmos fortes como AES-256 e BCrypt).
*   **Risco Associado:** **Crítico.** Violação direta da LGPD (Lei Geral de Proteção de Dados). O vazamento resulta em processos judiciais criminais e cíveis, multas milionárias aplicadas pelos órgãos reguladores e destruição imediata da reputação da marca.

#### SEG-02: Quebra de Autenticação e Controle de Acesso (Privilégios)
*   **Justificativa Didática:** O sistema possui dois perfis claros: Pacientes (leitura de médicos e escrita em suas próprias consultas) e Administradores (controle total de horários e visualização de dados de terceiros). O sistema deve isolar essas fronteiras de forma lógica e intransponível.
*   **Análise do Teste:** Testes de IdOR (*Insecure Direct Object Reference*). Tenta-se forçar o acesso a uma URL administrativa (ex: `/admin/dashboard`) usando uma conta de paciente comum, ou alterar o ID de uma consulta na requisição para tentar visualizar ou cancelar o agendamento de outra pessoa.
*   **Risco Associado:** **Alto.** Fraudes na agenda, sabotagem de horários médicos, cancelamentos indevidos em massa e exposição indevida da agenda confidencial dos profissionais de saúde.

#### SEG-03: Ciclo de Vida e Envenenamento de Sessão (*Session Management*)
*   **Justificativa Didática:** Quando um usuário faz login, o sistema gera um "token" (como um crachá digital). Se esse crachá durar para sempre ou não for destruído quando o usuário clica em "Sair", qualquer um que usar o mesmo dispositivo depois poderá reabsorver o acesso.
*   **Análise do Teste:** Validação do tempo de expiração (*timeout*) por inatividade (ex: deslogar após 15 minutos ocioso) e verificação de que o token foi completamente invalidado no servidor após o logout do usuário.
*   **Risco Associado:** **Médio.** Acesso indesejado a dados de saúde caso o paciente realize o agendamento em computadores de lan houses, hospitais ou dispositivos compartilhados e apenas feche a aba do navegador sem clicar em "Sair".

---

### 👥 2.3. Usabilidade
A usabilidade mede a facilidade com que um ser humano interage com o sistema para atingir seu objetivo de forma satisfatória e sem atritos.

#### USAB-01: Eficiência do Fluxo de Agendamento (Carga Cognitiva)
*   **Justificativa Didática:** O agendamento de uma consulta deve ser um processo livre de estresse. Se o usuário precisar passar por 10 telas diferentes, preencher formulários gigantescos e decifrar ícones confusos, o sistema falhou em sua missão principal de simplicidade.
*   **Análise do Teste:** Avaliação Heística de Nielsen e testes guiados com usuários reais. Contabiliza-se o número de cliques mínimos necessários para agendar e verifica-se a clareza da jornada visual.
*   **Risco Associado:** **Alto.** Abandono da plataforma. O cliente desiste de usar o meio digital e sobrecarrega o call center da clínica, aumentando os custos operacionais que a plataforma web deveria reduzir.

#### USAB-02: Engenharia de Mensagens de Erro e Prevenção de Falhas
*   **Justificativa Didática:** Erros acontecem (ex: tentar cancelar uma consulta faltando apenas 2 horas para o atendimento). O sistema não pode simplesmente exibir um código técnico abstrato como *"Error 403: Business Rule Violation"*. Ele deve educar o usuário sobre o que aconteceu e como proceder.
*   **Análise do Teste:** Forçar intencionalmente violações das regras de negócio e mapear todas as mensagens exibidas na tela, avaliando sua clareza, tom de voz e utilidade prática para a resolução do problema.
*   **Risco Associado:** **Médio.** Frustração extrema do usuário, que se sente impotente diante de um sistema que "parece quebrado". Isso gera uma percepção de má qualidade do produto e entope o suporte com dúvidas simples.

#### USAB-03: Acessibilidade Inclusiva (Universalidade)
*   **Justificativa Didática:** Plataformas médicas atendem a toda a população, o que inclui idosos com vista cansada, pessoas com daltonismo ou limitações motoras transitórias ou permanentes. O design não deve ser apenas bonito, deve ser legível para todos.
*   **Análise do Teste:** Verificação de contraste de cores seguindo as diretrizes WCAG (Web Content Accessibility Guidelines), testes de navegação usando apenas o teclado (sem mouse) e validação da leitura de tela por softwares de assistência.
*   **Risco Associado:** **Médio.** Exclusão social e perda de uma fatia significativa de clientes (especialmente o público idoso, que é o que mais consome serviços de saúde).

---

### 📱 2.4. Compatibilidade e Portabilidade
Garante que a experiência planejada seja entregue perfeitamente, não importando qual tecnologia o cliente final escolheu para acessar a internet.

#### COMP-01: Adaptabilidade e Responsividade Fluida em Telas Mobile
*   **Justificativa Didática:** A maior parte dos acessos modernos à internet ocorre por smartphones. Uma tabela de horários médicos que fica perfeita em um monitor de 24 polegadas pode ficar completamente espremida, cortada ou ilegível na tela de um celular de 5 polegadas.
*   **Análise do Teste:** Execução de testes em layouts responsivos utilizando diferentes resoluções de tela reais e simuladas (Viewport de smartphones iOS e Android), focando na área útil de toque dos botões.
* **Risco Associado:** **Alto.** Inviabilização do uso mobile. Se o botão de "Confirmar Consulta" ficar escondido para fora da tela ou for pequeno demais para ser clicado com o polegar, o sistema perde sua utilidade prática no dia a dia. 

#### COMP-02: Renderização Multicross-Browser (Multi-Navegadores) 
* **Justificativa Didática:** Embora o Chrome domine o mercado, muitos usuários utilizam o Safari (ecossistema Apple), o Edge (padrão do Windows) ou o Firefox. Motores de renderização diferentes interpretam códigos CSS e JavaScript modernos de maneiras ligeiramente distintas. 
* **Análise do Teste:** Execução paralela dos fluxos de cadastro e agendamento nos motores Blink (Chrome/Edge), WebKit (Safari) e Gecko (Firefox), garantindo comportamento idêntico em todos. 
* **Risco Associado:** **Médio.** Quebra isolada de funcionalidades. Um script de calendário pode funcionar perfeitamente no Chrome, mas não abrir ou travar completamente no Safari, fazendo com que usuários de iPhone não consigam escolher datas. 


