## 🧠 Capítulo 5 – Conceitos Fundamentais: Node.js

> "Node.js não é apenas uma tecnologia; é a ponte que transforma o JavaScript em uma ferramenta de alto desempenho no lado do servidor."

Neste capítulo, vamos mergulhar nos fundamentos do **Node.js**, entender seu funcionamento interno, suas características, vantagens e por que ele se tornou uma das tecnologias mais populares para desenvolvimento backend nos últimos anos.

------

### 🔍 O que é o Node.js

O **Node.js** é um ambiente de execução de JavaScript do lado do servidor, construído sobre o **motor V8 do Google Chrome**. Antes do Node.js, o JavaScript era restrito ao ambiente do navegador, sendo utilizado apenas para criar interações e comportamentos dinâmicos no frontend.

Com o surgimento do Node.js em 2009, tornou-se possível escrever **aplicações completas usando apenas JavaScript**, incluindo o backend. Isso unificou a stack de desenvolvimento e abriu caminho para o surgimento do JavaScript full stack.

### Características principais do Node.js:

- **Event-driven (dirigido a eventos)**: o Node é orientado a eventos, o que significa que ele reage a ações externas (requisições, cliques, timers, etc) sem bloquear o restante do sistema.
- **Non-blocking I/O (entrada/saída não bloqueante)**: permite realizar operações de leitura/escrita (como acessar banco de dados ou arquivos) sem travar a aplicação.
- **Single-threaded com event loop**: embora tenha uma única thread principal, o Node é capaz de lidar com múltiplas conexões simultaneamente graças ao seu loop de eventos assíncrono.
- **Alta performance**: o motor V8 compila o código JavaScript diretamente para código de máquina, o que melhora muito o desempenho.

#### Exemplo básico:

```js
// Exemplo de servidor HTTP simples com Node.js
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Olá, mundo!');
});

server.listen(3000, () => {
  console.log('Servidor rodando na porta 3000');
});
```

Esse código cria um servidor que responde com "Olá, mundo!" para qualquer requisição feita à porta 3000.

------

### ⚙️ Como o Node.js funciona (event loop, single-threaded)

#### 🧠 Event Loop (Laço de Eventos)

O **event loop** é o mecanismo que permite ao Node.js realizar **operações assíncronas** sem bloquear a thread principal. Ele monitora a fila de eventos e executa as funções de callback conforme elas estiverem prontas.

Por exemplo:

```js
console.log("Início");

setTimeout(() => {
  console.log("Timeout executado");
}, 2000);

console.log("Fim");
```

Saída esperada:

```
Início
Fim
Timeout executado
```

Mesmo com o `setTimeout` de 2 segundos, o Node continua executando o código sem esperar. Isso é o poder da **execução assíncrona**.

#### 🧵 Single-threaded

Embora o Node tenha apenas uma thread principal para executar JavaScript, ele delega tarefas pesadas (como leitura de arquivos e consultas ao banco) para **threads internas** gerenciadas pelo sistema e as traz de volta quando prontas. Esse modelo o torna **altamente eficiente para aplicações I/O intensivas** (como APIs e servidores).

------

### 🚀 Vantagens do Node.js para Backend

- **Mesma linguagem no frontend e backend**: torna o desenvolvimento mais ágil e a curva de aprendizado mais suave.
- **Alta escalabilidade**: ideal para aplicações com muitas conexões simultâneas, como redes sociais ou chats em tempo real.
- **Grande ecossistema**: com o `npm`, o Node oferece acesso a milhares de bibliotecas prontas para uso.
- **Comunidade ativa e vibrante**: documentação, tutoriais, fóruns e atualizações constantes.
- **Boa integração com bancos de dados**: especialmente os baseados em JSON como MongoDB, mas também com MySQL, PostgreSQL, SQLite e outros.

#### Casos de uso comuns:

- APIs RESTful
- Aplicações em tempo real (como chats, jogos online)
- Sistemas de filas e microserviços
- Ferramentas de linha de comando (CLI)

------

### ✅ Conclusão do Capítulo

Neste capítulo, você compreendeu:

- O que é o Node.js e como ele revolucionou o backend com JavaScript;
- O funcionamento do event loop e da natureza single-threaded do Node;
- As vantagens práticas e estratégicas de utilizar Node.js em seus projetos;

Nos próximos capítulos, veremos como utilizar bibliotecas e módulos importantes para construir um backend funcional e conectado ao banco de dados. O conhecimento da arquitetura e comportamento do Node será essencial para avançarmos com segurança.