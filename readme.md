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

# 2º Passo: Clonar o projeto do gitHub, criar configuração da API e testar
## Processo de clone do projeto
* Copiar a url do projeto no seu repositório 
* Abrir o gitBash em um local do computador
* Digitar o comando 'git clone' junto com a URL do seu repositório
```
git clone URL_REPOSITORIO
```
## NO GITBASH
### Acessar pasta
* Digitar o comando 'cd' e o nome do seu repositório
* cd (change directory): acessar outra pasta

```
cd NOME_REPOSITORIO
```
* DICA: ao digitar cd + as 3 primeiras letras do nome da pasta e clicar no enter ele acha a pasta
* OBS: Caso não saiba o nome de sua pasta de o comando 
```
git ls 
```
## Reinstalar os pacotes da aplicação
* Este comando irá recriar a pasta node_modules no projeto
```
npm i
```
## Criar arquivo .env na raiz do projeto
```
nano .env
```
* DIGITAR NA JANELA ABERTA PELO NANO
```
PORT = 3008
```
* Este arquivo é utilizada para armazenar as variáveis que serão reutilizadas na aplicação
* Com o comando nano, podemos criar e editar um arquivo pelo terminal
* Ctrl + o: Salvar o arquivo
* Enter: Confirmar
* Ctrl + x: Fechar o arquivo
* PORT 3008 --> Variável que contém a porta que o servidor estará rodando
* Esta arquivo .env não enviamos pro gitHub, pois contém informações sensíveis do sistema

# Adicionar arquivo .env no .gitignore
```
nano .gitignore
```
```
.env
```
Com o comando nano, podemos criar e editar um arquivo pelo terminal
* Ctrl + o: Salvar o arquivo
* Enter: Confirmar
* Ctrl + x: Fechar o arquivo
## ABRIR VSCODE
```
code .
```
## Criar arquivo de exemplo para para as variáveis necessárias da aplicação
* Como não enviamos o arquivo .env para o gitHub, precisamos criar o exemplo das variáveis necessárias da aplicação
* Este arquivo conterá apenas as variáveis, sem os valores correspondentes

```
nano .env.example
```

ADICIONAR NO ARQUIVO .ENV
```
PORT = 
```
## NO VSCODE
### Abrir o arquivo app.js e digitar o código
* Importar o pacote express (servidor), Importar o pacote dotenv, gerenciador de variáveis de ambiente, Instanciar o express na variável app.
```
const express = require('express');
const dotenv = require('dotenv').config();
const app = express();

```
*  Setar a porta do servidor a partir do arquivo .env
* O operador condicional '||' significa 'OU', caso não tenha a variável PORT, será utilizado o valor '3333'
```
app.set('port', process.env.PORT || 3333);
```
*  Exportar as configurações na variável app
```
module.exports = app;
```

### Abrir o arquivo server.js e digitar os códigos
* Importar o arquivo app
```
const app = require('./app');
```
* Importar a porta do servidor
```
const port = app.get('port');
```

#### Testar API com a função listen
* 1º parâmetro: passamos a porta do servidor
* 2º parâmetro: arrow function para retornar um console informando a porta que está rodando o servidor
```
app.listen(port, () => {
    console.log(`Running on port ${ port }!`);
});

```

## Comando para executar a API
#### Abrir o arquivo package.json e alterar a chave 'scripts
* Substituir o comando 'test' pelo comando 'start' na linha 7
```
"start":"nodemon src/server.js"
```

## NO GIT BASH
* npm run start
* SE APARECER O NÚMERO DA PORTA ESTÁ TUDO CERTO

## Atualizar projeto no gitHub
* Adicionar todos arquivos ao versionamento
```
git add .
```
* Salvar projeto e escrever comentário sobre o processo realizado
```
git commit -m 'configuração do projeto'
```
* Enviar os arquivos atualizados para o gitHub
```
git push
```

## Atualize a página no gitHub e verifique se os arquivos foram atualizados
* Com o projeto no servidor remoto podemos remover os arquivos na nossa máquina
```
cd ..
```
* Comando para acessar uma pasta anterior

Fechar o VSCode com o projeto aberto
```
rm -rf projetoBackend
```
- rm (remove): comando utilizado para apagar arquivo
- -r (recursive): apaga pastas e subpastas de forma recursiva
- -f (force): não pergunta confirmações
- projetoBackend: nome da pasta que contem os arquivos da aplicação
# 3º Passo: Clonar o projeto do gitHub, criar a configuração do arquivo de rotas
## Clonar projeto
* Acessar repositório do projeto no gitHub
* Clicar no botão verde '<> Code'
* Clicar no ícone para copiar a URL, conforme a imagem
* Abrir o gitBash em um local do computador
* Digitar o comando 'git clone' junto com a URL do seu repositório
```
git clone URL_REPOSITORIO
```
## Acessar pasta
* Digitar o comando 'cd' e o nome do seu repositório
* cd (change directory): acessar outra pasta
```
cd NOME_REPOSITORIO
```
## Reinstalar os pacotes da aplicação
```
npm i
```
* Este comando irá recriar a pasta node_modules no projeto

## Criar pastas dentro da pasta src
```
mkdir src/routes
```
* Criar arquivo dentro da pasta routes
```
touch src/routes/rotas.js
```
Responsável pelas rotas que serão acessadas na API
* Abrir Vscode
```
code .
```

## Abrir o arquivo rotas.js e digitar os códigos
```
// Importar o modulo de Router do express
const { Router } = require('express');

// Instanciar o Router na variável router
const router = Router();

router.get('/listar', (request, response) => {
    response.send('Método GET: listar informações');
});
router.post('/cadastrar', (request, response) => {
    response.send('Método POST: salvar informações');
});
router.put('/user/:id', (request, response) => {
    response.send('Método PUT: atualizar informações');
});
router.delete('/user/:id', (request, response) => {
    response.send('Método DELETE: remover informações');
});

module.exports = router;
```
## Abrir o arquivo app.js e adicionar o código
```
const router = require('./routes/rotas');
```
* Precisamos importar o arquivo de rotas nas configurações da API
* Habilitar as rotas na aplicação
* Esta linha deve inserida depois da criação da variável app
```
app.use('/api', router);
```
## Atualizar projeto no gitHub
* Adicionar todos arquivos ao versionamento
```
git add .
```
* Salvar projeto e escrever comentário sobre o processo realizado
```
git commit -m 'rotas do projeto'
```
* Enviar os arquivos atualizados para o gitHub
```
git push
```
Com o projeto no servidor remoto podemos remover os arquivos na nossa máquina
```
cd ..
```
* Comando para acessar uma pasta anterior
* Fechar o VSCode com o projeto aberto
```
rm -rf projetoBackend
```