# 1º Passo: Projeto
## Criar pasta e organizar estrutura
Criar pasta para a aplicação
```
mkdir projetoBackend
```
 Acessar a pasta
```
cd projetoBackend
```
Criar um arquivo para documentar o projeto
```
touch readme.md
```
Iniciar o gerenciador de pacotes NODE
```
npm init -y
```
Instalar os pacotes: Express, Nodemon e Dotenv
```
npm i express nodemon dotenv
```
 Abrir no VSCODE
```
code .
```
Criar aquivo Gitignore
```
nano .gitignore
```
* Com o comando nano, podemos criar e editar um arquivo pelo terminal
* Ctrl + o: Salvar o arquivo
* Enter: Confirmar
* Ctrl + x: Fechar o arquivo
* Este arquivo é utilizado para ignorar o envio de pastas e arquivos pro gitHub

Adicionar no arquivo .gitignore o nome da pasta criada após a instalação dos pacotes
```
node_modules
```
Criar pasta SRC
```
mkdir src
```
Criar arquivos dentro da pasta src
```
touch src/app.js
```
* Arquivo responsável de criar a configuração da API
```
touch src/server.js
```
* Arquivo responsável em receber as configurações da aplicação e rodar a API


Criar pastas dentro da pasta src
```
mkdir src/config
```
* Pasta para gerenciar a conexão com o banco de dados
```
mkdir src/controllers
```
* Pasta para gerenciar as requisições das rotas e conexão com banco de dados
```
mkdir src/routes
```
* Pasta para gerenciar as rotas da API

Validar estrutura do projeto

* Confira se a pasta do seu projeto esta igual a imagem com as pastas e arquivos
```
{
  "name": "projetobackend",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "dotenv": "^16.3.1",
    "express": "^4.18.2",
    "nodemon": "^3.0.1"
  }
}
```
Enviar estrutura do projeto para o gitHub
```
git config
```
*  Inicializar o gerenciador de arquivos .git
```
git init
```
 Verificar config
```
git config -l
```
 Se der erro

* Informar o seu nome e email
* Altere o campo 'FIRST_NAME' e coloque o seu nome
* Altere o campo 'EMAIL@EXAMPLE.COM' e coloque o seu email do gitHub

```
git config --global user.name "FIRST_NAME"
```
```
 git config --global user.email "EMAIL@EXAMPLE.COM"
```
* Verificar arquivos que serão enviados ao gitHub
```
git status
```
* Adicionar todos arquivos ao versionamento
```
git add .
```
* Salvar projeto e escrever comentário sobre o processo realizado
```
git commit -m 'estrutura do projeto'
```
* Criar um novo repositório no gitHub
* Clicar no ponto indicado na imagem para copiar a URL do repositório

De volta ao terminal, executar o comando para definir a branch main
```
git branch -M main
```
* Informar o repositório que queremos enviar os arquivos
* Colar a URL do seu repositório copiada
```
git remote add origin COLAR_URL
```
* Enviar os arquivos para o gitHub
```
git push -u origin main
```

Atualize a página no gitHub e verifique se os arquivos foram enviados
* Com o projeto no servidor remoto podemos remover os arquivos na nossa máquina
```
cd ..
```
* Comando para acessar uma pasta anterior
* Fechar o VSCode com o projeto aberto
```
rm -rf projetoBackend
```