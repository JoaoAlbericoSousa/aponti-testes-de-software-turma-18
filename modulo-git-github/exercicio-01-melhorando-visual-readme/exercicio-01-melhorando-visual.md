# 📚 Exercício 1: Melhorando o Visual do README
 
Demonstração do uso de formatação básica em Markdown para títulos, listas e estilo de texto.

## 🛠️ Recursos Aplicados
*   **Negrito** e *Itálico* para dar ênfase.
*   Listas numeradas e com marcadores.

---
*Nota: Linha horizontal utilizada para separação lógica de conteúdos.*

# 🛠️ Guia Prático de Git e GitHub: Entendendo as Listas

Este documento serve como um exemplo prático de como utilizar listas numeradas e listas com marcadores (além de sublistas) em Markdown, utilizando tópicos essenciais sobre controle de versão.

---

## 📌 1. Fluxo de Trabalho Inicial do Git (Lista Numerada)

As listas numeradas são ideais para processos que exigem uma ordem cronológica ou passos sequenciais. Abaixo está o passo a passo para iniciar um repositório local e enviá-lo para a nuvem:

1. **`git init`** 📥: Inicializa um novo repositório Git local na pasta atual do seu projeto.
2. **`git status`** 🔍: Verifica o estado atual dos seus arquivos (quais foram modificados, criados ou deletados).
3. **`git add .`** ➕: Adiciona todas as modificações da pasta para a *Staging Area* (preparação para o commit).
4. **`git commit -m "mensagem"`** 💾: Grava as alterações salvas na *Staging Area* com uma mensagem descritiva.
5. **`git branch -M main`** 🌿: Define o nome da sua ramificação principal como `main`.
6. **`git remote add origin <url>`** 🔗: Vincula o seu repositório local ao repositório remoto criado no GitHub.
7. **`git push -u origin main`** 🚀: Envia os seus commits locais para o GitHub pela primeira vez.

---

## 📌 2. Principais Recursos do GitHub (Lista com Marcadores e Sublista)

As listas com marcadores são perfeitas para agrupar itens que não possuem uma ordem de execução obrigatória. As sublistas ajudam a detalhar pontos específicos de cada item.

* **Repositories (Repositórios)** 📁: Espaço onde o código do seu projeto fica armazenado.
  * **Public**: Qualquer pessoa na internet pode ver o código.
  * **Private**: Apenas você e colaboradores autorizados possuem acesso.
* **Pull Requests (PRs)** 🔀: Propostas de alterações de código enviadas de uma ramificação para outra.
  * Permite a revisão de código (*code review*) por outros membros da equipe.
  * Executa testes automatizados antes da integração final.
* **Issues** 🪲: Ferramenta para rastrear tarefas, relatar bugs, gerenciar melhorias ou planejar o projeto.
* **GitHub Actions** 🤖: Automação de fluxos de trabalho (CI/CD) diretamente do seu repositório.
  * Compilação automática do código.
  * Publicação direta em servidores de hospedagem.
* **GitHub Pages** 🌐: Serviço gratuito para hospedar sites estáticos diretamente a partir de um repositório.

---

### 💡 Dica de Sintaxe Markdown

Para criar as listas acima no seu editor, basta utilizar a seguinte estrutura simples:

*   **Para listas numeradas:** Utilize o número seguido de ponto e espaço (`1. `, `2. `).
*   **Para listas com marcadores:** Utilize o asterisco seguido de espaço (`* `) ou hífen (`- `).
*   **Para sublistas:** Insira um recuo de **4 espaços** ou **1 tabulação** antes do marcador do subitem.
