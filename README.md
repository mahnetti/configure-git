# Configurando o GIT no Ubuntu/Debian

Vou mostrar como fazer as configurações inicias do git para sua máquina Ubuntu (por linha de código).

Caso queira parar outras distros consulte aqui (https://git-scm.com/download/linux).

Índice:
- Instalando o GIT
- Configurando o GIT
- Autenticando o GIT

1.Instalando o GIT

Para dar início abra seu terminal e digite a seguinte linha para baixar a última versão estável:
apt update
sudo apt-get install git

Para verificar a versão baixada:
git --version

2. Configurando o GIT

Para escolher seu nome de usuário, trocando "seu_nome_aqui" pelo nome de usuário:
git config --global user.name seu_nome_aqui

Agora, para configurar seu e-mail, trocando o "seu@email.com"
git config --global user.email seu@email.com

3.Autenticando o GIT

Para você conseguir a comunicação entre a sua máquina e o GitHub é necessário cadastrar uma chave de segurança:

- Chave SSH
- Chave HTTP(recomendada)

Aqui vou focar na chave SSH, caso tenha interesse na chave HTTP consulte aqui (https://docs.github.com/pt/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls).

Ainda no terminal (certifique-se que não está em outra pasta desejada):
ssh-keygen -t ed25519 -C "seu@email.com"

Caso apareça a seguinte mensagem, pressione ENTER:
> Enter a file in which to save the key (/home/YOU/.ssh/ALGORITHM):[Press enter]

Troque "seu@email.com" pelo mesmo e-mail que você usou na configuração acima, esse comando já gera uma chava SSH. Para cadastrar essa nova chave precisamos rodar em 2º plano o ssh-agente, para isso temos:

eval "$(ssh-agent -s)"
> Agent pid 59566

Se no seu ambiente não rodar você pode tentar:
xec ssh-agent bash ou exec ssh-agent zsh

Para poder copiar sua chave, use:
$ cat ~/.ssh/id_ed25519.pub

Isso vai gerar uma chave que deve começar com ssh-rsa

Agora você vai logar na sua conta do GitHub e clicar no menu superior direito (onde tem sua foto) e clicar em configurações

![image](https://github.com/mahnetti/configure-git/assets/85520887/cf58663a-8cd7-4753-9685-c00d403d0399)

Na sessão de acesso, selecione SSH e GPG Key
![image](https://github.com/mahnetti/configure-git/assets/85520887/c72c1d95-f29b-4341-a7f4-69fbd241322c)

Você pode dar o nome a sua chave, por exemplo "Computador Pessoal", "Computador Empresa"




Fontes:
https://git-scm.com/downloads
