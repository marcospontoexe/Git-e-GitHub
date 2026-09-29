# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Visão geral

Repositório de estudo sobre Git e GitHub, em português (PT-BR). Não há código-fonte, build, lint nem testes. O conteúdo é uma apostila em Markdown e slides de aula em PDF.

## Índice

- [README.md](README.md): apostila do curso. Cobre conceitos (VCS centralizado × distribuído, Git × GitHub, história), o conteúdo da pasta `.git`, fluxo básico e mensagens de commit (Conventional Commits), desfazer alterações, repositório remoto, branches (uso no dia a dia e nomenclatura), GitHub (fork, issues, pull requests passo a passo incluindo aprovação do próprio PR, Pages, segurança), e termina com uma referência rápida de comandos. Os exemplos de `git cat-file` usam objetos reais do commit `3e7d0fe`, com o e-mail do autor omitido. Cada tópico é uma seção `##` listada no Sumário. Comandos ficam entre crases e os diagramas são em Mermaid. Os links para os PDFs usam o caminho codificado (`%20`, `%C3%A9` etc.), porque os nomes têm espaços e acentos. Ao adicionar uma aula, atualize a tabela "Material das aulas".
- [slides-aulas/](slides-aulas/): PDFs nomeados `NN-Título.pdf`, feitos pelo Prof. Gustavo Guanabara (Curso em Vídeo). Os termos dele exigem manter a referência ao original, por isso não remova a seção "Créditos" do README. A numeração tem lacunas de propósito (hoje existem 01–03, 11 e 12, porque nem todas as aulas foram adicionadas). Não renumere os arquivos existentes. Uma aula nova usa o número dela na sequência do curso.
- [guia-markdown.pdf](guia-markdown.pdf): guia de referência da sintaxe Markdown.

## Ambiente (Windows / PowerShell)

O `git` **não está no PATH**. Use o git que vem com o GitHub Desktop. O caminho muda a cada versão, então resolva-o assim:

```powershell
$git = (Get-ChildItem "$env:LOCALAPPDATA\GitHubDesktop\app-*\resources\app\git\cmd\git.exe" | Sort-Object LastWriteTime -Descending | Select-Object -First 1).FullName
& $git status
```

- Remote `origin`: https://github.com/marcospontoexe/Git-e-GitHub.git, branch `main`.
- [.gitattributes](.gitattributes) usa `* text=auto` (normalização LF). Os PDFs são commitados direto, sem Git LFS.

---

# Regra: Persistência de Contexto (Handoff entre sessões)

> Cole esta regra no `CLAUDE.md` do projeto.

---

## Objetivo

Garantir que nenhum trabalho se perca quando a sessão atual se tornar demasiado longa. O agente deve gravar todo o estado da sessão num ficheiro de handoff, de forma que **qualquer outro chat consiga retomar exatamente de onde parou**, com o mesmo contexto.
---

## Gatilho

Execute o procedimento de salvamento abaixo **antes de continuar qualquer tarefa** sempre que uma das seguintes condições for atingida:
1. A conversa prolongar-se por muitas interações (aproximando-se do limite prático da janela de contexto).
2. Uma funcionalidade ou milestone importante for concluída.
3. O utilizador disser explicitamente: `salvar contexto`, `handoff` ou `checkpoint`.

---

## Procedimento de salvamento

1. **Termine** a tarefa atual.
2. Crie ou atualize o arquivo **`CONTEXTO.md`** na raiz do projeto.
   - Se já existir, **atualize** as seções em vez de duplicar (mantenha o histórico relevante, remova o que já foi superado).
   - Sempre atualize o campo de data/hora e o número da sessão.
3. Preencha **todas** as seções do template abaixo. Não deixe seções vazias — escreva "nenhum" quando não houver conteúdo.
4. Confirme ao usuário que o contexto foi salvo e informe o caminho do arquivo.
5. **Gestão do CONTEXTO.md:**  Mantenha o CONTEXTO.md enxuto. Ele segue o template abaixo, mas cada seção deve ter só o resumo. Quando um tópico precisar de mais detalhe (uma decisão longa, um passo a passo, etc.), escreva-o num ficheiro em DOCS/ na raiz do projeto e coloque no CONTEXTO.md apenas o link para ele. O objetivo é não sobrecarregar a janela de contexto ao ler o CONTEXTO.md. Se precisar de mais informações sobre um tópico, abra o ficheiro específico em DOCS/.

---

## Template do `CONTEXTO.md`

```markdown
# CONTEXTO DA SESSÃO

- **Última atualização:** AAAA-MM-DD HH:MM
- **Sessão nº:** N
- **Status geral:** (em andamento | bloqueado | pronto para revisão)

## 1. Objetivo da tarefa
Descrição em 1–3 frases do que estamos tentando alcançar (o "porquê").

## 2. Já feito ✅
- Itens concluídos, com o(s) arquivo(s) afetado(s).
- Ex.: "Implementado endpoint POST /login em `src/auth.py`"

## 3. Em andamento 🔧
- O que estava sendo feito no momento do checkpoint.
- Em qual arquivo/linha parei e qual era o próximo passo imediato.

## 4. Próximos passos (planejado) 📋
- Lista ordenada do que falta fazer.
- Quanto mais específico, melhor (arquivo, função, comportamento esperado).

## 5. Decisões e raciocínio 🧠
- Escolhas técnicas feitas e o porquê.
- Alternativas descartadas (para evitar refazer a análise).
- Suposições assumidas.

## 6. Estado do projeto / ambiente
- Arquivos-chave e o papel de cada um.
- Branch git atual, alterações não commitadas, migrations pendentes, etc.
- Variáveis de ambiente ou dependências relevantes.

## 7. Bloqueios e pendências ⚠️
- Erros não resolvidos, dúvidas para o usuário, decisões aguardando aprovação.

## 8. Comandos úteis
- Comandos para rodar/testar/buildar o projeto.
- Ex.: `npm run dev`, `pytest tests/`, etc.

## 9. Como retomar
Instrução direta para o próximo chat: "Leia este arquivo e continue a partir
da seção 3 / passo X."
```

---

## Como retomar em um novo chat

No início de qualquer nova sessão, o agente deve:

1. Verificar se existe o ficheiro `CONTEXTO.md` na raiz do projeto .
2. Se existir, **lê-lo por completo antes de qualquer outra ação**.
3. Resumir ao utilizador em 2–3 linhas onde o trabalho parou e qual é o próximo passo, e então continuar.

> Comando sugerido para o utilizador iniciar um novo chat:
> **"Leia o `CONTEXTO.md` e continue de onde a sessão anterior parou."**

---

## Boas práticas

- **Escreva para um estranho:** o próximo chat não tem memória nenhuma; seja explícito.
- **Caminhos absolutos ou relativos à raiz**, nunca referências vagas ("aquele arquivo").
- **Não salve segredos** (tokens, senhas, chaves) no `CLAUDE.md` e `CONTEXTO.md`.
- **Um arquivo por projeto:** mantenha `CONTEXTO.md` enxuto; arquive versões antigas em `CONTEXTO.arquivo.md` se necessário.
- **Commit opcional:** se o usuário usar git, ofereça commitar o `CONTEXTO.md` para que ele persista entre máquinas.
- **Feedback de alterações:** Caso algum ficheiro seja alterado durante a sessão, informe sempre qual o ficheiro e o que foi alterado no final de cada mensagem.
- **referenciar diretórios e arquivos atraves de links:** Sempre que se referir a um diretório ou arquivo local, use link e não backticks.
