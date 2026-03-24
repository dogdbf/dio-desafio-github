# Desafio de projeto sobre Git/GitHub

Repositório criado para desenvolvimento do desafio de projeto sobre Git/Github 

### ### Comandos importantes do Git

```bash
git init  
```

Inicializa um repositório Git na pasta atual.  

```bash
git add .  
```

Adiciona todos os arquivos para a área de staging.  

```bash
git commit -m "mensagem"  
```

Salva as alterações no repositório local.  

```bash
git status  
```

Mostra o estado atual do repositório.  

```bash
git clone <url>  
```

Clona um repositório remoto.  

```bash
git push origin main  
```

Envia commits para o repositório remoto.  

```bash
git pull origin main  
```

Atualiza o repositório local com alterações remotas.

### Trobleshooting

- Acesse o gitbash;
  
  ```ssh-keygen -t ed25519 -C "e-mail que usa no github"
  ssh-keygen -t ed25519 -C "e-mail que usa no github"
  ```

- Será perguntado sobre onde salvar, verifique o local e navegue até a pasta.

- Enter passphrase (empty for no passphrase): criar uma senha, caso queira, ou pressione _enter_ para seguir, serão exibidas as mensagens:

Your identification has been saved in /c/Users/nome usuario/.ssh/id_ed25519

Your public key has been saved in /c/Users/nome usuario/.ssh/id_ed25519.pub

- Acesse a pasta em que suas chaves foram salvas, navegando até ela pela CLI, exemplo:
  
  ```cd /c/Users/Usuário/.ssh/```
  cd /c/Users/Usuario/.ssh/
  ```

- Para verificar os arquivos, digite 
  
  ```
  ls
  ```
  
   Os arquivos abaixo devem ser listados:

**_id_ed25519 id_ed25519.pub**

- Dê o comando abaixo para visualizar o conteúdo da chave pública gerada nesse procedimento:

```cat id_ed25519.pub
cat id_ed25519.pub
```

- Irá aparecer uma chave com sequência de algarismos e o email cadastrado 

ssh-ed25519 (....)+e-mail (essa chave publica)

- Feito isso, acesse seu GitHub e vá nas _Configurações_ e depois em ssh e GPG Keys

- Clique em _New SSH Key_

- Dê um nome à chave gerada

- em _Key Type_ , selecione Authentication Key 

- Cole a chave gerada no Git

- Retorne ao Git e dê o comando abaixo para iniciar o agente SSH e configurar automaticamente o ambiente do seu terminal
  
  ```eval $(ssh-agent -s) 
  eval $(ssh-agent -s)
  ```

- Para finalizar a configuração do ssh, dê o comando abaixo para adicionar a chave privada ao agente SSH e permitir autenticação sem precisar digitar a senha a cada conexão.
  
  ```ssh-add id_ed25519
  ssh-add id_ed25519
  ```
  
  Após esse procedimento, seu ambiente estará configurado para utilizar autenticação via SSH, permitindo executar comandos como `git clone`, `git pull` e `git push` sem a necessidade de informar credenciais a cada operação.
  
  **Fiquem à vontade para entrar em contato em caso de dúvidas.**
  
  
  
  ## Links Úteis

[Sintaxe básica Markdown](https://ajuda.memberkit.com.br/como-funciona/guia-basico-de-markdown?gad_source=1&gad_campaignid=22306642075&gclid=Cj0KCQjwpv7NBhCzARIsADkIfWwHmtQvPHCNlvP3UNhtbN2Y7gy5jIeoT9RUIoySuKCOFw_aAuffn68aAlU9EALw_wcB)

[Download Git](https://git-scm.com/)

**Douglas B Ferreira**, 22 de Março de 2026
