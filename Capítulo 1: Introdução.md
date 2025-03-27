## 🧠 Capítulo 1 – Introdução

> "Por trás de cada clique, há uma lógica que trabalha silenciosamente para transformar intenções em ações. Isso é o poder do backend."

### O que é Backend

Em uma aplicação web moderna, geralmente trabalhamos com duas grandes partes: o **frontend** e o **backend**. Enquanto o frontend é a camada visível da aplicação — aquilo que o usuário vê e interage, como botões, menus, cores e animações — o **backend** é o cérebro por trás da operação.

O backend é responsável por **processar dados**, **executar regras de negócio**, **interagir com bancos de dados** e **retornar respostas ao frontend**. Ele é como a parte invisível de um iceberg: essencial, robusto e, muitas vezes, mais complexo do que parece.

Algumas responsabilidades típicas do backend incluem:

- Autenticação e controle de acesso
- Validação de dados recebidos do frontend
- Armazenamento e recuperação de dados em bancos de dados
- Comunicação com APIs externas
- Geração de respostas em formatos como JSON ou XML

Por exemplo, imagine que um usuário faz login em um sistema. O frontend envia os dados (e-mail e senha) para o backend. O backend então:

1. Valida os dados recebidos;
2. Busca o usuário no banco de dados;
3. Verifica se a senha está correta;
4. Gera um token de autenticação;
5. Retorna esse token ao frontend, que o usará para acessar áreas protegidas do sistema.

Sem o backend, a aplicação seria apenas uma "casca bonita" sem inteligência.

### Por que usar Node.js com MySQL

O **Node.js** é uma plataforma construída sobre o motor V8 do Google Chrome, que permite executar código JavaScript no servidor. Já o **MySQL** é um sistema de gerenciamento de banco de dados relacional (SGBD) amplamente usado, gratuito e robusto.

A combinação Node.js + MySQL é poderosa por diversas razões:

- **JavaScript no servidor e no cliente**: isso simplifica o aprendizado e o desenvolvimento, já que podemos usar a mesma linguagem no frontend e no backend.
- **Alta performance**: o Node.js é baseado em eventos e não bloqueante, o que permite lidar com muitas requisições simultaneamente.
- **Comunidade ativa e vasto ecossistema**: tanto o Node.js quanto o MySQL possuem excelente documentação e suporte da comunidade.

Exemplo prático:

Imagine uma aplicação de lista de tarefas (to-do list). O usuário pode adicionar, editar e excluir tarefas. O Node.js será responsável por receber essas requisições, processar os dados e interagir com o MySQL para salvar e recuperar as tarefas.

```json
// Requisição que o backend receberia ao adicionar uma nova tarefa:
{
  "titulo": "Estudar Node.js",
  "descricao": "Ler o capítulo 1 do tutorial",
  "concluida": false
}
```

O backend, ao receber esse JSON, o interpretaria, validaria os dados e executaria um comando SQL para inserir a nova tarefa no banco de dados.

### O desafio de não usar frameworks (inicialmente)

Um dos objetivos deste tutorial é mostrar como criar um backend com Node.js e MySQL **sem depender de frameworks prontos**, NestJS, Fastify, etc. Mas por quê?

Ao construir do zero:

- Você entende **profundamente como o Node.js funciona**;
- Aprende a **criar rotas manualmente** e a **tratar requisições HTTP**;
- Desenvolve um senso crítico para **avaliar quando e por que usar um framework no futuro**.

Frameworks são ótimos e poupam tempo, mas escondem muita coisa importante para quem está começando. Este tutorial parte do princípio de que entender o "por baixo dos panos" é essencial para formar desenvolvedores backend completos.

Posteriormente, utilizaremos o framework Express — uma ferramenta leve e poderosa — apenas depois de compreender bem o funcionamento interno de um servidor Node.js.

### Conclusão deste capítulo

Neste capítulo, você conheceu:

- O papel e a importância do backend em uma aplicação web;
- As vantagens de utilizar Node.js em conjunto com MySQL;
- A razão de iniciarmos o tutorial sem frameworks: para construir uma base sólida de conhecimento.

Nos próximos capítulos, vamos começar a preparar o ambiente de desenvolvimento e dar os primeiros passos com código real. Mas antes disso, respire fundo: você está prestes a dominar os bastidores da web!