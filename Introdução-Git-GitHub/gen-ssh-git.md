# 🔗 Git & GitHub - Guia Prático Completo

Guia prático sobre Git e GitHub com foco em controle de versão, colaboração e fluxos de trabalho profissionais.

---

## 📚 Sumário

1. [Conceitos Fundamentais](#-conceitos-fundamentais)
2. [Configuração Inicial](#-configura%C3%A7%C3%A3o-inicial)
3. [Comandos Essenciais](#-comandos-essenciais)
4. [Branches e Fluxos de Trabalho](#-branches-e-fluxos-de-trabalho)
5. [Configuração SSH](#-configura%C3%A7%C3%A3o-ssh)
6. [Colaboração e Integração](#-colabora%C3%A7%C3%A3o-e-integra%C3%A7%C3%A3o)
7. [Boas Práticas](#-boas-pr%C3%A1ticas)
8. [Troubleshooting](#-troubleshooting)
9. [Referências](#-refer%C3%AAncias)

---

## 🎯 Conceitos Fundamentais

### O que é Git?

**Git** é um sistema de controle de versão distribuído que permite:

- Rastrear alterações no código
- Trabalhar em paralelo (branches)
- Colaborar com outros desenvolvedores
- Reverter mudanças quando necessário

### Ciclo de vida dos arquivos

```
Working Directory  →  Staging Area  →  Repository
(arquivos locais)   (git add)       (git commit)
```

---

## ⚙️ Configuração Inicial

### 1. Instalar Git

**Windows:**

- 🔗 [Redirecting&hellip;](https://git-scm.com/download/win)

**Linux/Ubuntu:**

bash

```bash
sudo apt install git -y
```

**macOS:**

bash

```bash
brew install git
```

---

### 2. Configuração de identidade

Defina seu nome e email (obrigatório):

bash

```bash
git config --global user.name "Douglas Ferreira"
git config --global user.email "seu-email@github.com"
```

✅ O `--global` aplica para todos os repositórios. Remova-o para apenas um repo.

---

### 3. Verificar configuração

bash

```bash
git config --list
```

---

### 4. Configurações úteis adicionais

bash

```bash
# Editor padrão para mensagens de commit
git config --global core.editor "nano"

# Mais legível no log
git config --global log.decorate short

# Cores ativadas
git config --global color.ui true
```

---

## 🚀 Comandos Essenciais

### Criar um novo repositório

bash

```bash
git init
```

Cria um repositório Git na pasta atual (cria pasta `.git`).

---

### Clonar um repositório existente

bash

```bash
git clone https://github.com/usuario/repositorio.git
```

Baixa um repositório remoto para sua máquina.

---

### Ver status do repositório

bash

```bash
git status
```

Mostra:

- ✅ Arquivos rastreados
- ❌ Arquivos não rastreados
- ⚠️ Arquivos modificados

---

### Adicionar arquivos para staging

Adicionar um arquivo:

bash

```bash
git add arquivo.txt
```

Adicionar todos os arquivos:

bash

```bash
git add .
```

Adicionar apenas tipos específicos:

bash

```bash
git add *.js
```

---

### Commit (salvar alterações)

Commit básico:

bash

```bash
git commit -m "Descrição clara da alteração"
```

Commit com mais detalhes (abre editor):

bash

```bash
git commit
```

Commit direto (sem staging):

bash

```bash
git commit -am "mensagem"  # apenas arquivos já rastreados
```

---

### Ver histórico de commits

bash

```bash
git log
```

Versão mais compacta:

bash

```bash
git log --oneline
```

Com gráfico de branches:

bash

```bash
git log --graph --oneline --all
```

---

### Enviar commits para repositório remoto

bash

```bash
git push origin main
```

Força push (⚠️ use com cuidado):

bash

```bash
git push origin main --force
```

---

### Atualizar repositório local com alterações remotas

bash

```bash
git pull origin main
```

Equivalente a: `git fetch` + `git merge`

---

### Ver diferenças

Diferenças não salvas:

bash

```bash
git diff
```

Diferenças entre commits:

bash

```bash
git diff commit1 commit2
```

---

## 🌿 Branches e Fluxos de Trabalho

### O que é uma branch?

Uma **branch** é uma linha de desenvolvimento independente. A branch padrão é geralmente `main` (antes era `master`).

---

### Listar branches

bash

```bash
git branch
```

Ver também branches remotas:

bash

```bash
git branch -a
```

---

### Criar uma branch

bash

```bash
git branch minha-feature
```

---

### Mudar para uma branch

bash

```bash
git checkout minha-feature
```

Ou mais moderno (Git 2.23+):

bash

```bash
git switch minha-feature
```

---

### Criar e mudar de uma vez

bash

```bash
git checkout -b minha-feature
```

Ou:

bash

```bash
git switch -c minha-feature
```

---

### Renomear branch (local)

bash

```bash
git branch -m nome-antigo nome-novo
```

---

### Deletar branch

Local:

bash

```bash
git branch -d minha-feature
```

Forçar (⚠️ cuidado):

bash

```bash
git branch -D minha-feature
```

Remota:

bash

```bash
git push origin --delete minha-feature
```

---

### Merge (integrar branches)

Mesclar `minha-feature` na `main`:

bash

```bash
git checkout main
git merge minha-feature
```

---

### Git Flow (fluxo de trabalho profissional)

```
main (produção)
  ↑
release/1.0.0 (preparação)
  ↑
develop (integração)
  ↑
feature/... (desenvolvimento)
hotfix/... (correções críticas)
```

**Recomendação:**

- `main` → código estável em produção
- `develop` → integração de features
- `feature/nome` → novas funcionalidades
- `hotfix/nome` → correções críticas

---

## 🔐 Configuração SSH

### ✅ Por que usar SSH?

- ✅ Mais seguro que HTTPS
- ✅ Sem precisar digitar senha a cada comando
- ✅ Padrão em ambientes profissionais

---

### Passo 1: Gerar chave SSH

bash

```bash
ssh-keygen -t ed25519 -C "seu-email@github.com"
```

⚠️ Se seu sistema não suporta Ed25519, use RSA:

bash

```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@github.com"
```

---

### Passo 2: Localização da chave

Quando perguntado, pressione **Enter** para aceitar o local padrão:

```
~/.ssh/id_ed25519
```

---

### Passo 3: Passphrase (opcional)

```
Enter passphrase (empty for no passphrase):
```

Você pode:

- ✅ Criar uma senha (mais seguro)
- ✅ Deixar vazio (pressionar Enter)

---

### Passo 4: Verificar as chaves

bash

```bash
cd ~/.ssh
ls -la
```

Você deve ver:

- `id_ed25519` (chave privada - 🔒 NUNCA compartilhe)
- `id_ed25519.pub` (chave pública - pode compartilhar)

---

### Passo 5: Copiar chave pública

bash

```bash
cat ~/.ssh/id_ed25519.pub
```

Copie todo o conteúdo (começa com `ssh-ed25519` e termina com seu email).

---

### Passo 6: Adicionar no GitHub

1. Acesse [Sign in to GitHub · GitHub](https://github.com/settings/keys)
2. Clique em **New SSH key**
3. **Title**: Dê um nome (ex: "Laptop Douglas")
4. **Key type**: Authentication Key
5. **Key**: Cole a chave pública copiada
6. Clique em **Add SSH key**

---

### Passo 7: Testar a conexão

bash

```bash
ssh -T git@github.com
```

Se sucesso, você verá:

```
Hi seu-usuario! You've successfully authenticated, but GitHub does not provide shell access.
```

---

### Passo 8: Inicializar o agente SSH

bash

```bash
eval $(ssh-agent -s)
```

Adicionar a chave privada:

bash

```bash
ssh-add ~/.ssh/id_ed25519
```

---

### Clonar repositório com SSH

Após SSH configurado, use URLs SSH:

bash

```bash
git clone git@github.com:usuario/repositorio.git
```

Em vez de HTTPS:

bash

```bash
git clone https://github.com/usuario/repositorio.git
```

---

## 🤝 Colaboração e Integração

### Fluxo típico de colaboração

```
1. git clone <repo>
2. git checkout -b feature/minha-funcionalidade
3. [faz alterações]
4. git add .
5. git commit -m "feat: descreve a funcionalidade"
6. git push origin feature/minha-funcionalidade
7. [abre Pull Request no GitHub]
8. [revisão de código]
9. [merge na main/develop]
```

---

### Sincronizar com repositório upstream

Se trabalha com fork:

bash

```bash
# Adicionar referência ao repositório original
git remote add upstream https://github.com/usuario-original/repo.git

# Buscar atualizações
git fetch upstream

# Integrar na sua branch local
git merge upstream/main
```

---

### Rebase (reorganizar histórico)

⚠️ Use com cuidado (muda histórico):

bash

```bash
git rebase main
```

Mais seguro que merge em alguns casos.

---

## ✅ Boas Práticas

### 1. Mensagens de commit claras

❌ **Ruim:**

```
git commit -m "ajustes"
git commit -m "corrigido"
```

✅ **Bom:**

```
git commit -m "feat: adiciona autenticação OAuth"
git commit -m "fix: corrige validação de email"
git commit -m "docs: atualiza README com exemplos"
```

**Padrão Conventional Commits:**

```
<tipo>(<escopo>): <descrição>

<body opcional>
<footer opcional>
```

Tipos: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

---

### 2. .gitignore

Crie um arquivo `.gitignore` para excluir arquivos:

```
# Dependências
node_modules/
__pycache__/
*.pyc

# Ambientes
.env
.venv

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db

# Build
dist/
build/
*.log
```

---

### 3. Commits atômicos

Cada commit deve fazer UMA coisa:

❌ **Ruim:**

```
git commit -m "adiciona login, corrige bug, atualiza docs"
```

✅ **Bom:**

```
git commit -m "feat: implementa formulário de login"
git commit -m "fix: corrige validação de campos"
git commit -m "docs: adiciona instruções de uso"
```

---

### 4. Evite commits diretos na main

✅ Sempre trabalhe em branches:

bash

```bash
git checkout -b feature/nova-coisa
# [faz alterações]
git push origin feature/nova-coisa
# [abre PR, revisão, merge]
```

---

### 5. Sincronize frequentemente

bash

```bash
git pull origin main
```

Evita conflitos no futuro.

---

### 6. Revise antes de pushar

bash

```bash
git diff HEAD~1
```

Verifique o que vai enviar.

---

## 🐛 Troubleshooting

### Problema: "fatal: not a git repository"

**Causa:** Você não está dentro de um repositório Git.

**Solução:**

bash

```bash
git init
```

Ou:

bash

```bash
cd caminho/do/repositorio
```

---

### Problema: "branch main não existe"

**Causa:** Repositório antigo usa `master`.

**Solução 1 - Renomear branch:**

bash

```bash
git branch -M master main
```

**Solução 2 - Usar master:**

bash

```bash
git push origin master
```

**Solução 3 - Criar main:**

bash

```bash
git checkout -b main
git push origin main
```

---

### Problema: "everything up-to-date" (mas alterações não foram enviadas)

**Causa:** Você não fez commit das alterações.

**Solução:**

bash

```bash
git add .
git commit -m "descrição"
git push origin main
```

---

### Problema: Conflito de merge

**Quando ocorre:** Duas pessoas modificam a mesma linha.

**Solução manual:**

bash

```bash
git status  # veja arquivos com conflito
```

Abra o arquivo e procure por:

```
<<<<<<< HEAD
seu código
=======
código da outra pessoa
>>>>>>> branch-name
```

Escolha qual manter, delete os marcadores, e:

bash

```bash
git add .
git commit -m "resolve conflito em arquivo.js"
git push origin main
```

---

### Problema: Preciso reverter um commit

Desfazer último commit (mantém mudanças):

bash

```bash
git reset HEAD~1
```

Desfazer último commit (descarta mudanças):

bash

```bash
git reset --hard HEAD~1
```

---

### Problema: Esqueceu de adicionar arquivo no último commit

bash

```bash
git add arquivo-esquecido.js
git commit --amend --no-edit
git push origin main --force-with-lease
```

⚠️ Use `--force-with-lease` em vez de `--force` (mais seguro).

---

### Problema: SSH não funciona

**Teste a conexão:**

bash

```bash
ssh -T git@github.com
```

**Se falhar:**

bash

```bash
# Verificar se ssh-agent está rodando
eval $(ssh-agent -s)

# Adicionar chave novamente
ssh-add ~/.ssh/id_ed25519

# Testar novamente
ssh -T git@github.com
```

---

### Problema: Digitar senha toda vez

**Solução 1 - SSH (recomendado):**

bash

```bash
git remote set-url origin git@github.com:usuario/repo.git
```

**Solução 2 - Credential Helper:**

bash

```bash
git config --global credential.helper store
```

---

## 📚 Referências

### Documentação Oficial

- 🔗 [Git Documentation](https://git-scm.com/doc)
- 🔗 [GitHub Docs](https://docs.github.com)
- 🔗 [Conventional Commits](https://www.conventionalcommits.org/)

### Materiais Complementares

- 🔗 [Pro Git Book (Gratuito)](https://git-scm.com/book/pt-BR/v2)
- 🔗 [GitHub Flow Guide](https://guides.github.com/introduction/flow/)
- 🔗 [Markdown Syntax](https://guides.github.com/features/mastering-markdown/)

### Ferramentas Úteis

- 🔗 [GitHub Desktop](https://desktop.github.com/) (interface gráfica)
- 🔗 [GitKraken](https://www.gitkraken.com/) (interface avançada)
- 🔗 [VS Code Git Integration](https://code.visualstudio.com/docs/editor/versioncontrol)

---

## 🎯 Dica Profissional

**Em ambientes reais:**

1. **Nunca faça push direto na `main`** → sempre use branches + PRs
2. **Use SSH** para segurança
3. **Escreva commits claros** → facilita revisar histórico
4. **Sincronize frequentemente** → evita conflitos
5. **Use `.gitignore`** → não commite arquivos sensíveis
6. **Code review** → sempre revise PRs de colegas

---

✍️ **Autor:** Douglas Bezerra Ferreira  
📅 **Data:** 31 de Março de 2026  
🏷️ **Versão:** 1.0 (Refatorado e profissional)

---

💡 **Se esse guia te ajudou, compartilha ou contribui no repositório!** ⭐
