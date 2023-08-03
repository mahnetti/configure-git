# Configurando o GIT no Ubuntu/Debian

Vou mostrar como fazer as configurações inicias do git para sua máquina Ubuntu (por linha de código), para fins educativos e de consulta.
Caso queira para outras distros ou dúvidas consulte aqui (https://git-scm.com/download/linux).

# Índice:
  ### **1. Instalando o GIT**<br>**2. Configurando o GIT**<br> **3. Autenticando o GIT**

## 1.Instalando o GIT

Para dar início abra seu terminal e digite a seguinte linha para baixar a última versão estável:<br>
```sudo apt update```<br>
```sudo apt-get install git```

Para verificar a versão baixada:<br>
```git --version```

## 2. Configurando o GIT

Para escolher seu nome de usuário, trocando *"seu_nome_aqui"* pelo nome de usuário:<br>
```git config --global user.name seu_nome_aqui```

Agora, para configurar seu e-mail, trocando o *"seu@email.com"*<br>
```git config --global user.email seu@email.com```

Para você conseguir a comunicação entre a sua máquina e o GitHub é necessário cadastrar uma chave de segurança:

- Chave SSH
- Chave HTTP

Aqui vou focar na chave SSH, caso tenha interesse na chave HTTP consulte aqui (https://docs.github.com/pt/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls).

Ainda no terminal (certifique-se que não está em outra pasta desejada):

```ssh-keygen -t ed25519 -C "seu@email.com"```<br>
*Troque "seu@email.com" pelo mesmo e-mail que você usou na configuração acima.*

Caso apareça as seguintes mensagem:

```> Enter a file in which to save the key (/home/YOU/.ssh/ALGORITHM):```<br>
 *Pressione Enter*
 
```> Enter passphrase (empty for no passphrase):```<br>
*Para cadastrar uma senha de acesso a chave, caso não queira, apenas clique em enter*

Agora precisamos rodar em 2º plano o ssh-agente, para isso temos:

```
eval "$(ssh-agent -s)"
> Agent pid 59566
```

Se no seu ambiente não rodar você pode tentar:
```xec ssh-agent bash``` ou ```exec ssh-agent zsh```

Para adicionar sua chave ao ssh-agent, use:<br>
```ssh-add ~/.ssh/id_ed25519```

Isso vai gerar uma chave que deve começar com ssh-rsa, para poder visualiza-la, rode:<br>
```cat ~/.ssh/id_ed25519.pub```<br>
Agora, copie o código para usarmos no próximo passo.


## 3. Autenticando o GIT

Agora você vai logar na sua conta do GitHub e clicar no menu superior direito (onde tem sua foto) e clicar em configurações<br>
<img src="https://github.com/mahnetti/configure-git/assets/85520887/cf58663a-8cd7-4753-9685-c00d403d0399" width="200">

Na sessão de acesso, selecione SSH e GPG Key
<img src="(https://github.com/mahnetti/configure-git/assets/85520887/c72c1d95-f29b-4341-a7f4-69fbd241322c)" width="200">


![image](https://github.com/mahnetti/configure-git/assets/85520887/c72c1d95-f29b-4341-a7f4-69fbd241322c)

Você pode dar o nome a sua chave, por exemplo "Computador Pessoal", "Computador Empresa". E agora estamos preparados ṕara começar a trabalhar com o GitHub.


Para erros, dúvidas, outras distros acesse a documentação original citada no início desse documento. Conteúdo está referenciado nos links do documento.
