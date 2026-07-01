# 🗺️ Guia de Organização do Portfólio FAP

Este documento estabelece as diretrizes de organização, cronologia e padronização para o repositório do programa FAP (Formação Acelerada de Programadores), promovido pela aponti.

---

## 📅 Cronologia dos Módulos e Conteúdos

O portfólio está estruturado para refletir a evolução do aprendizado ao longo do programa, dividido em três grandes etapas:

### 1️⃣ Módulo 1: Soft Skills
Desenvolvimento de competências comportamentais essenciais para o mercado de tecnologia.
*   **Componentes:** Videoaulas, conteúdo de apoio (slides de aula) e materiais complementares.

### 2️⃣ Módulo 2: Git e GitHub
Fundamentos de versionamento de código, colaboração e documentação de projetos.
*   **Componentes:** Videoaulas, conteúdo de apoio (slides), materiais complementares e atividades práticas.
*   **Atividades Entregues:**
    *   **Atividade 1 - Atividade GitHub:** Pesquisa, experimentação prática e registro reflexivo sobre os principais conceitos e comandos do Git/GitHub.
    *   **Atividade 2 - Avaliação do Módulo:** Aplicação prática de boas práticas de versionamento, documentação e personalização deste repositório.

### 3️⃣ Módulo 3: Testes de Software
Aplicação técnica de estratégias de garantia de qualidade (QA) e automação.
*   **Componentes:** Planejamento, execução de testes manuais e scripts de automação.

---

## 📂 Estrutura de Pastas Recomendada

Para organizar os materiais de apoio, slides, atividades e código, utilize a estrutura de diretórios abaixo:

```text
├── 🧠 mod01-soft-skills/         # Slides, resumos e reflexões do Módulo 1
├── 🔀 mod02-git-github/        # Slides e entregas das atividades práticas do Módulo 2
│   ├── 📝 atividade-01/       # Pesquisa e registro reflexivo
│   └── 💻 atividade-02/       # Configurações e testes de versionamento
├── 🪲 mpd03-testes-software/     # Casos de teste e automações do Módulo 3
│   ├── 📑 testes-manuais/
│   ├── 🌐 automacao-web/
│   └── ⚙️ testes-api/
└── 📄 README.md               # Documentação principal do portfólio

```

---

## 📝 Regras de Organização e Documentação

### 1. Documentação por Conteúdo Estudado (Obrigatório)
Para facilitar a visualização do progresso e a avaliação de cada etapa, você deve criar um arquivo Markdown (`.md`) individual para cada tópico estudado. 

**Exemplos de nomenclatura padrão:**
*   `README-GIT.md`
*   `README-REPOSITORIO.md`
*   `README-SOFT-SKILLS.md`

### 2. Mensagens de Commit (Conventional Commits)
Mantenha o histórico do Git limpo utilizando prefixos claros:
*   `feat:` Para a entrega de novas atividades ou scripts de teste.
*   `docs:` Para criação ou atualização de arquivos Markdown (como os resumos de conteúdo).
*   `fix:` Para correção de links, textos ou bugs em códigos de automação.

---

## 🚀 Diretrizes Avançadas para o Portfólio (Recomendações Extras)

*Adicione estas seções conforme avança no Módulo 3 para demonstrar maturidade técnica:*

*   **Matriz de Rastreabilidade:** Uma tabela simples que associa os Requisitos do Sistema aos Casos de Teste criados.
*   **Estratégia de Testes:** Explicação de como dividiu seus testes (Manuais vs Automatizados) e como gerenciou a massa de dados.
*   **Pré-requisitos de Execução:** Um passo a passo rápido ensinando qualquer recrutador a clonar o repositório, instalar dependências (ex: `npm install`) e rodar os testes criados.
