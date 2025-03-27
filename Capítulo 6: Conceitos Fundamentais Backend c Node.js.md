## 🧠 Capítulo 6 – Conceitos Fundamentais: Backend c/ Node.js

### Principais Bibliotecas e Utilizações

> "Escolher as ferramentas certas é tão importante quanto saber usá-las — no desenvolvimento backend, as bibliotecas certas economizam tempo, reduzem erros e aumentam a produtividade."

Neste capítulo, vamos conhecer as bibliotecas e módulos essenciais para o desenvolvimento backend com Node.js. Algumas são **módulos nativos** (já vêm com o Node.js), enquanto outras precisam ser **instaladas via npm**, mas são amplamente utilizadas em projetos profissionais. Entender suas funções e como utilizá-las é parte fundamental para o sucesso de qualquer aplicação backend moderna.

------

### 📦 Módulos Nativos do Node.js

O Node.js vem com diversos módulos nativos — ou seja, que **não precisam ser instalados**. Eles cobrem funcionalidades essenciais para manipulação de arquivos, criação de servidores, leitura de diretórios, entre outros.

#### 🔹 `http`

Responsável por criar servidores HTTP. Fundamental para lidar com requisições e respostas sem depender de frameworks.

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Servidor Node.js básico');
});

server.listen(3000, () => {
  console.log('Servidor rodando na porta 3000');
});
```

#### 🔹 `fs` (File System)

Permite ler, escrever, deletar e manipular arquivos e diretórios no sistema de arquivos.

```js
const fs = require('fs');

fs.writeFile('mensagem.txt', 'Olá, mundo!', (err) => {
  if (err) throw err;
  console.log('Arquivo criado com sucesso!');
});
```

#### 🔹 `path`

Fornece utilitários para trabalhar com caminhos de arquivos e diretórios de forma multiplataforma.

```js
const path = require('path');

const caminho = path.join(__dirname, 'arquivos', 'log.txt');
console.log(caminho);
```

------

### 📦 Bibliotecas Populares via npm

Estas bibliotecas **não fazem parte do core do Node.js**, mas são amplamente utilizadas no desenvolvimento backend profissional. São instaladas com o comando:

```bash
npm install nome-da-biblioteca
```

#### 🔹 `mysql2`

Biblioteca para conectar aplicações Node.js a bancos de dados MySQL (ou MariaDB). Rápida, moderna e com suporte a Promises e Prepared Statements.

```js
const mysql = require('mysql2');

const conexao = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'senha',
  database: 'meubanco'
});

conexao.connect((err) => {
  if (err) throw err;
  console.log('Conectado ao MySQL!');
});
```

#### 🔹 `dotenv`

Permite carregar variáveis de ambiente a partir de um arquivo `.env`, útil para ocultar dados sensíveis como senhas e portas.

Instalação:

```bash
npm install dotenv
```

Uso:

```js
require('dotenv').config();

console.log(process.env.DB_HOST);
```

Conteúdo do arquivo `.env`:

```
DB_HOST=localhost
DB_USER=root
DB_PASS=123456
```

#### 🔹 `nodemon`

Ferramenta de desenvolvimento que reinicia automaticamente a aplicação Node.js sempre que um arquivo é salvo. Evita a necessidade de parar e rodar manualmente o servidor.

Instalação global:

```bash
npm install -g nodemon
```

Uso:

```bash
nodemon index.js
```

#### 🔹 `express`

Embora este tutorial inicie sem frameworks, o **Express** é o mais popular para construção de APIs RESTful com Node.js. Ele simplifica a criação de rotas, middlewares e tratamento de erros. Será abordado futuramente, após a compreensão do módulo `http`.

```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Bem-vindo à API!');
});

app.listen(3000, () => console.log('Servidor Express rodando!'));
```

------

### 🧠 Outras Bibliotecas Úteis (menções)

- **bcrypt**: para criptografar senhas;
- **jsonwebtoken**: para autenticação com tokens (JWT);
- **cors**: para configurar requisições entre diferentes origens;
- **axios**: cliente HTTP para fazer requisições a outras APIs;
- **moment** ou **dayjs**: manipulação de datas e horários.

Essas bibliotecas não serão utilizadas neste início de projeto, mas fazem parte do dia a dia de qualquer desenvolvedor backend Node.js.

------

### ✅ Conclusão do Capítulo

Neste capítulo, você aprendeu:

- A diferença entre módulos nativos e bibliotecas instaláveis via npm;
- Como utilizar `http`, `fs` e `path` no Node.js;
- A importância e aplicações práticas de `mysql2`, `dotenv` e `nodemon`;
- Uma introdução ao Express, que será explorado em breve.

Com essas ferramentas à disposição, estamos prontos para começar a explorar os protocolos HTTP e construir as primeiras rotas do nosso backend!