# CONTEXTO DA SESSÃO

- **Última atualização:** 2026-09-27 21:34
- **Sessão nº:** 1
- **Status geral:** pronto para revisão

## 1. Objetivo da tarefa
Transformar este repositório de estudo (curso de Git e GitHub do Curso em Vídeo) numa apostila clara e completa, e preparar o repositório para ser trabalhado pelo Claude Code em sessões futuras.

## 2. Já feito ✅
- Criado o [CLAUDE.md](CLAUDE.md): visão geral, índice dos arquivos, como achar o `git` (não está no PATH) e a regra de handoff.
- Regra de handoff atualizada no `~/.claude/CLAUDE.md` global e copiada para o [CLAUDE.md](CLAUDE.md) do projeto (os dois textos são idênticos).
- [README.md](README.md) reescrito do zero, com base nos slides de [slides-aulas/](slides-aulas/). Tem sumário, tabela das aulas, conceitos, fluxo, desfazer alterações, remoto, branches, GitHub/segurança, referência rápida e créditos ao autor dos slides.
- Corrigidos os erros do README antigo: `git add` sem argumento, item de lista vazio, `.java` descrito como binário e `git revert` descrito como forma de descartar edições locais.

## 3. Em andamento 🔧
- nenhum (aguardando revisão do usuário sobre o novo README)

## 4. Próximos passos (planejado) 📋
1. O usuário revisa o [README.md](README.md) e pede ajustes, se houver.
2. Commitar `README.md`, `CLAUDE.md` e `CONTEXTO.md` (e fazer push, se o usuário quiser).
3. Quando os slides das aulas 04 a 10 forem adicionados, incluir cada um na tabela "Material das aulas" do README e, se trouxerem assuntos novos, criar a seção correspondente.

## 5. Decisões e raciocínio 🧠
- README voltado a quem estuda o curso (PT-BR). Os tópicos seguem os slides, com complementos práticos (config, `.gitignore`, `restore`, conflitos, 2FA atual, autenticação por token/SSH).
- As datas da tabela de história seguem as fontes históricas, não os slides: CVS em 1990 (o slide diz 1985) e o Linux adotando o BitKeeper em 2002.
- Os links para os PDFs usam URL codificada. Conferido com `git ls-files` que os nomes estão em UTF-8 NFC (é = `%C3%A9`).
- A seção "Créditos" é obrigatória: os termos do Prof. Gustavo Guanabara exigem manter a referência ao material original.
- Diagramas em Mermaid (`flowchart` e `gitGraph`): o GitHub renderiza nativamente. O preview do VS Code precisa de extensão.

## 6. Estado do projeto / ambiente
- Branch `main`, remoto `origin` = https://github.com/marcospontoexe/Git-e-GitHub.git.
- Alterações não commitadas: [README.md](README.md) (modificado), [CLAUDE.md](CLAUDE.md) e [CONTEXTO.md](CONTEXTO.md) (novos).
- O `git` não está no PATH; usar o git do GitHub Desktop (comando na seção 8).
- Não há build, lint nem testes (repositório só de conteúdo).

## 7. Bloqueios e pendências ⚠️
- nenhum

## 8. Comandos úteis
```powershell
$git = (Get-ChildItem "$env:LOCALAPPDATA\GitHubDesktop\app-*\resources\app\git\cmd\git.exe" | Sort-Object LastWriteTime -Descending | Select-Object -First 1).FullName
& $git status
& $git -c core.quotepath=true ls-files   # mostra os bytes dos nomes com acento
```

## 9. Como retomar
Leia este arquivo e o [CLAUDE.md](CLAUDE.md). Depois pergunte ao usuário se o README foi aprovado e siga a partir da seção 4, passo 2.
