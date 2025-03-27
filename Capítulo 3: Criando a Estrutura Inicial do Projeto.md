## 🧠 Capítulo 3 – Criando a Estrutura Inicial do Projeto

> "Organização não é apenas estética — é o alicerce que sustenta a escalabilidade e a manutenção de qualquer aplicação."

Neste capítulo, daremos início ao desenvolvimento prático do nosso backend com Node.js. Antes de qualquer funcionalidade, precisamos preparar a **estrutura base do projeto**, que será a espinha dorsal para todo o código que virá a seguir. Este momento é crucial para garantir **clareza, organização, reaproveitamento de código e facilidade de manutenção**.

------

### 🚀 Iniciando com `npm init`

O `npm` (Node Package Manager) é o gerenciador de pacotes oficial do Node.js. Ele nos permite instalar bibliotecas, scripts e ferramentas de apoio. Também é responsável por gerenciar as **dependências** e **metadados** do projeto por meio do arquivo `package.json`.

#### 🔧 Criando o diretório do projeto

Primeiramente, abra o terminal e crie um diretório para o projeto:

```bash
mkdir backend-nodejs
cd backend-nodejs
```

#### 🧱 Inicializando o projeto com npm

Agora, dentro da pasta do projeto, execute:

```bash
npm init -y
```

Esse comando cria automaticamente um arquivo `package.json` com configurações padrão. Esse arquivo é como a identidade do projeto e armazena:

- Nome e versão do projeto
- Scripts customizados para execução
- Lista de dependências
- Licença e descrição

Você pode editá-lo manualmente ou, se preferir, rodar `npm init` (sem `-y`) para preencher cada campo interativamente.

Exemplo de `package.json` gerado:

```json
{
  "name": "backend-nodejs",
  "version": "1.0.0",
  "description": "Projeto backend com Node.js e MySQL",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

------

### 📁 Organização básica de diretórios e arquivos

A estrutura de pastas é essencial para manter a organização do projeto. Mesmo que ele comece pequeno, devemos estruturá-lo pensando em crescimento e escalabilidade.

#### 🗂️ Estrutura inicial sugerida:

```plaintext
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

Vamos entender melhor o propósito de cada pasta:

- **index.js**: ponto de entrada da aplicação. É onde o servidor será iniciado.
- **routes/**: define os caminhos (endpoints) da API e para onde cada requisição será direcionada.
- **controllers/**: arquivos responsáveis pela lógica das requisições (ex: salvar usuário, buscar tarefas).
- **models/**: camada de acesso ao banco de dados. Contém funções SQL ou integrações com bibliotecas como `mysql2`.
- **config/**: armazena configurações reutilizáveis como parâmetros de conexão, portas, etc.
- **.env**: armazena informações sensíveis (senha do banco, porta do servidor, etc.) sem deixar visível no repositório.

> ⚠️ Importante: o arquivo `.env` nunca deve ser versionado. Adicione-o ao `.gitignore`.

------

### 📝 Criando o arquivo principal: `index.js`

Dentro do diretório raiz, crie um novo arquivo chamado `index.js`. Esse será o ponto inicial do servidor. Por enquanto, podemos adicionar um código simples apenas para validar que o ambiente está funcional:

```js
console.log('Servidor iniciado com sucesso!');
```

Agora, execute o projeto pela primeira vez:

```bash
node index.js
```

Se tudo estiver correto, a mensagem "Servidor iniciado com sucesso!" será exibida no terminal.

------

### 📌 Conclusão do Capítulo

Neste capítulo, você:

- Criou a pasta do projeto e inicializou com `npm`;
- Compreendeu o papel do `package.json`;
- Estruturou pastas e arquivos pensando em organização e escalabilidade;
- Criou o primeiro arquivo do projeto (`index.js`) e testou a execução.

A partir daqui, podemos seguir para os conceitos fundamentais do backend e do Node.js antes de implementarmos funcionalidades reais. Essa base bem organizada será nossa aliada para escrever um código limpo, coeso e fácil de manter.