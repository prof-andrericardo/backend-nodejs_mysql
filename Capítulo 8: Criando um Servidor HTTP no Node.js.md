## 🧠 Capítulo 8 – Criando um Servidor HTTP com Node.js

> "Todo backend começa com uma porta aberta — é ali que o servidor escuta, responde e dá vida às aplicações."

Neste capítulo, vamos construir nosso primeiro servidor HTTP utilizando **Node.js**, estruturando o projeto com base em uma arquitetura modular e seguindo boas práticas de organização de código. Começaremos com a configuração do ambiente, instalação de dependências essenciais, e então criaremos um servidor Express totalmente funcional.

Nosso objetivo é garantir uma base sólida para o desenvolvimento backend, com organização clara, separação de responsabilidades e automatização do fluxo de trabalho com o **Nodemon**. Cada passo será descrito de forma minuciosa, com explicações abrangentes e exemplos práticos para facilitar o aprendizado.

------

### 🗂️ Estrutura Inicial Sugerida

A estrutura abaixo foi pensada para separar as responsabilidades do projeto, facilitar a escalabilidade e promover a reutilização de código:

```
backend-nodejs/
├── node_modules/           # Bibliotecas instaladas (gerado pelo npm)
├── package.json            # Configurações e dependências do projeto
├── index.js                # Arquivo principal que inicializa o servidor
├── routes/                 # Rotas da aplicação
├── controllers/            # Lógica de controle para cada rota
├── models/                 # Acesso ao banco de dados
├── config/                 # Configurações gerais (ex: conexão com MySQL)
├── .env                    # Variáveis de ambiente (não versionado)
└── README.md               # Documentação inicial do projeto
```

Essa organização é amplamente adotada em projetos Node.js reais e facilitará muito o entendimento dos próximos capítulos, como a integração com banco de dados e implementação de regras de negócio.

------

### 🔹 Etapa 1: Inicializando o Projeto

1. Crie a pasta do projeto e acesse-a:

```bash
mkdir backend-nodejs && cd backend-nodejs
```

2. Inicie o projeto com `npm init -y` para gerar o arquivo `package.json`:

```bash
npm init -y
```

3. Crie os diretórios que compõem a estrutura modular do projeto:

```bash
mkdir src src/routes src/controllers src/models src/config
```

> 🧠 A pasta `src` conterá toda a lógica da aplicação. Manter esse padrão ajuda a organizar melhor o projeto à medida que ele cresce.

4. Crie o arquivo principal `index.js` na raiz do projeto. Ele será responsável por carregar o app e iniciar o servidor.

------

### 🔹 Etapa 2: Instalando Dependências

#### Instalando o Express

O Express será o responsável por lidar com as requisições HTTP e o roteamento da aplicação.

```bash
npm install express --save
```

#### Instalando o Nodemon (ambiente de desenvolvimento)

O Nodemon reinicia o servidor automaticamente sempre que houver mudanças no código.

```bash
npm install nodemon -D
```

Instalando o Dotenv (variáveis de ambiente)

Dotenv é um módulo de dependência zero que carrega variáveis de ambiente de um arquivo .env para process.env.

```bash
# install locally (recommended)
npm install dotenv --save
```

------

### 🔹 Etapa 3: Criando a Base do Servidor com Express

#### Arquivo `index.js`

```js
const app = require('./src/app');
const dotenv = require('dotenv');

dotenv.config();

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});
```

> 📌 O `dotenv` carrega as variáveis de ambiente definidas no arquivo `.env`, como a porta do servidor. Isso torna o projeto mais flexível e seguro.

#### Arquivo `.env`

```
PORT=3000
```

> 🔐 Lembre-se de adicionar `.env` ao `.gitignore` para evitar que informações sensíveis sejam versionadas.

#### Arquivo `src/app.js`

```js
const express = require('express');
const routes = require('./routes');

const app = express();

app.use(express.json()); // Permite receber dados em JSON
app.use(routes);         // Define o uso das rotas da aplicação

module.exports = app;
```

> 🎯 Aqui configuramos o `express.json()` para lidar com requisições com corpo JSON, e conectamos o arquivo de rotas à aplicação.

#### Arquivo `src/routes/index.js`

```js
const express = require('express');
const router = express.Router();

// Rota padrão da aplicação
router.get('/', (req, res) => {
  res.status(200).send('Hello World com Express na estrutura inicial sugerida!');
});

module.exports = router;
```

> ✨ Podemos adicionar outras rotas nesse mesmo arquivo ou dividi-las por funcionalidades à medida que o projeto crescer.

------

### 🔹 Etapa 4: Automatizando com Nodemon

Abra o arquivo `package.json` e modifique a seção `scripts`:

```json
"scripts": {
  "dev": "nodemon index.js"
}
```

Agora, podemos rodar o projeto com:

```bash
npm run dev
```

> 🔁 O Nodemon monitora os arquivos do projeto. Ao detectar uma alteração, ele reinicia automaticamente o servidor.

Exemplo: altere a resposta da rota `/` e salve o arquivo. Você verá no terminal que o servidor foi reiniciado automaticamente.

------

### 🧪 Testando com Navegador ou Insomnia

Com o servidor rodando, abra o navegador ou o Insomnia e acesse:

```
http://localhost:3000/
```

Se tudo estiver correto, você verá:

```
Hello World com Express na estrutura inicial sugerida!
```

> 🧪 O Insomnia é especialmente útil para testar métodos POST, PUT e DELETE com corpo JSON.

------

### ✅ Conclusão do Capítulo

Neste capítulo, você:

- Estruturou o projeto seguindo uma arquitetura modular e escalável;
- Instalou e configurou o Express como servidor web;
- Criou uma rota padrão utilizando boas práticas;
- Utilizou o Nodemon para automatizar a reinicialização do servidor durante o desenvolvimento;
- Testou a aplicação localmente com navegador ou Insomnia.

---

### ✅ Referências

- [Express](https://expressjs.com/)
- [HTTP](https://en.wikipedia.org/wiki/HTTP)
- [Insomnia](https://insomnia.rest/)
- [Nodemon](https://www.npmjs.com/package/nodemon)
- [Dotenv](https://www.npmjs.com/package/dotenv)
