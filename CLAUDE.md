# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Visão geral

Repositório de estudo sobre Git e GitHub, em português (PT-BR), baseado no curso gratuito do Curso em Vídeo (Prof. Gustavo Guanabara). Não há código-fonte, build, lint nem testes. O conteúdo é uma apostila em Markdown e slides de aula em PDF.

### Histórico

- **2021:** repositório criado (licença MIT, autor marcos daniel santana) com um README curto de comandos básicos e os slides do curso.
- **Setembro de 2026:** README reescrito do zero e ampliado com o Claude Code, a partir dos slides. As dúvidas do autor durante o estudo viraram seções da apostila: centralizado × distribuído, pasta `.git`, nomes de branches e commits, uso de branches, issues, pull requests e GitHub Pages.

## Índice

- [README.md](README.md): apostila do curso. Cobre:
  - conceitos: VCS centralizado × distribuído, Git × GitHub, história;
  - o que há dentro da pasta `.git` (objetos blob/tree/commit, refs, reflog);
  - fluxo básico e mensagens de commit (Conventional Commits);
  - desfazer alterações e repositório remoto;
  - branches: para que servem, uso no dia a dia, nomenclatura e conflitos;
  - GitHub: fork, issues, pull requests passo a passo (incluindo aprovar o próprio PR), Pages e segurança da conta;
  - referência rápida de comandos e créditos.

  Cada tópico é uma seção `##` listada no Sumário. Comandos ficam entre crases e os diagramas são em Mermaid. Ao adicionar uma aula, atualize a tabela "Material das aulas".
- [slides-aulas/](slides-aulas/): PDFs nomeados `NN-Título.pdf`, feitos pelo Prof. Gustavo Guanabara. A numeração tem lacunas de propósito (hoje existem 01–03, 11 e 12, porque nem todas as aulas foram adicionadas). Não renumere os arquivos existentes. Uma aula nova usa o número dela na sequência do curso.
- [guia-markdown.pdf](guia-markdown.pdf): guia de referência da sintaxe Markdown.

## Decisões editoriais

- **Público:** quem estuda o curso, em PT-BR. As dúvidas do autor são respondidas no próprio README (é a apostila dele), com um resumo no chat.
- **Créditos obrigatórios:** os termos do Prof. Gustavo Guanabara permitem usar os slides para aprendizado, desde que mantida a referência ao original. Não remova a seção "Créditos" do README.
- **Fatos acima dos slides:** a tabela de história segue as fontes históricas quando os slides divergem (CVS em 1990, e não 1985; o Linux adotou o BitKeeper em 2002).
- **Links para os PDFs:** usam o caminho codificado (`%20`, `%C3%A9` etc.), porque os nomes têm espaços e acentos. Os nomes estão em UTF-8 NFC; confira com `git -c core.quotepath=true ls-files`.
- **Exemplos de `git cat-file`:** usam objetos reais do commit `3e7d0fe`, para o leitor poder reproduzir. O e-mail do autor aparece como `<...>`.
- **Convenções nos exemplos:** Conventional Commits em português, com verbo no presente (`feat: adiciona ...`). Branches no formato `tipo/descricao-curta`, com os mesmos tipos.
- **Interface do GitHub:** os nomes de botões seguem a interface atual. Onde ela varia (Review changes / Submit review), os dois nomes aparecem.
- **Recomendações para repositório solo:** commitar direto na `main` é aceitável, e não se deve exigir aprovações de PR (o autor não pode aprovar o próprio PR).
- **Mermaid:** renderiza no github.com, mas não no preview do VS Code sem extensão nem no GitHub Pages sem um script extra.
- **GitHub Pages:** avaliado e não adotado para este repositório, porque duplicaria o README, os diagramas Mermaid não renderizam e os `.md` internos virariam páginas. Para praticar Pages, a sugestão é um site pessoal em `marcospontoexe.github.io`.

## Ambiente (Windows / PowerShell)

O `git` **não está no PATH**. Use o git que vem com o GitHub Desktop. O caminho muda a cada versão, então resolva-o assim:

```powershell
$git = (Get-ChildItem "$env:LOCALAPPDATA\GitHubDesktop\app-*\resources\app\git\cmd\git.exe" | Sort-Object LastWriteTime -Descending | Select-Object -First 1).FullName
& $git status
```

- Remote `origin`: https://github.com/marcospontoexe/Git-e-GitHub.git, branch `main`.
- [.gitattributes](.gitattributes) usa `* text=auto` (normalização LF). Os PDFs são commitados direto, sem Git LFS.
- A regra de handoff entre sessões está no `~/.claude/CLAUDE.md` global. O arquivo de handoff `CONTEXTO.md` fica só na máquina local: está no [.gitignore](.gitignore) e não vai para o GitHub.
