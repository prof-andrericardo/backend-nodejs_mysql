## 🧠 Capítulo 7 – Conceitos Fundamentais: Métodos HTTP

> "A web é uma linguagem de pedidos e respostas — e os métodos HTTP são os verbos que nos permitem conversar com os servidores."

Neste capítulo, vamos estudar de forma **abrangente e detalhada** os **métodos HTTP**, fundamentais para a construção de qualquer sistema web moderno. Entender esses métodos é essencial para compreender como o backend interage com o frontend e como os dados trafegam entre cliente e servidor. Também aprenderemos sobre os principais **códigos de status HTTP** e faremos simulações práticas usando arquivos JSON como banco de dados em memória.

------

### 🌐 O que são Métodos HTTP

O protocolo HTTP (Hypertext Transfer Protocol) define a comunicação entre clientes (navegadores, apps, scripts) e servidores. Ele segue uma arquitetura baseada em **requisições e respostas**. Toda vez que acessamos um site, clicamos em um botão, enviamos um formulário ou solicitamos algum dado, estamos fazendo uma requisição HTTP.

Essas requisições são classificadas por **métodos**, também chamados de **verbos HTTP**, que expressam a intenção da ação:

- `GET`: Solicita dados (leitura)
- `POST`: Envia dados (criação)
- `PUT`: Atualiza dados (edição completa)
- `PATCH`: Atualiza parcialmente (não será foco agora)
- `DELETE`: Remove dados (exclusão)

Esses métodos são utilizados no desenvolvimento de **APIs RESTful** — um padrão de arquitetura amplamente utilizado na construção de sistemas modernos.

------

### 📁 JSON Base para Exemplos

Vamos trabalhar com uma estrutura simulada de dados local (sem banco de dados), armazenada em um arquivo chamado `usuarios.json`. Essa abordagem ajuda a visualizar claramente o comportamento de cada método HTTP antes de conectarmos ao MySQL.

#### Conteúdo do arquivo `usuarios.json`:

```json
[
  { "id": 1, "nome": "Alice", "email": "alice@email.com" },
  { "id": 2, "nome": "Bruno", "email": "bruno@email.com" },
  { "id": 3, "nome": "Carla", "email": "carla@email.com" }
]
```

Esse JSON será a base para nossos exemplos em todos os métodos explicados a seguir.

------

### 🔹 Método GET – Leitura de dados

O `GET` é utilizado para **consultar informações no servidor**. É o método mais seguro e mais utilizado nas aplicações web. Ele **não deve alterar** os dados no servidor.

#### Casos comuns de uso:

- Listar todos os usuários
- Buscar um único usuário por ID

#### Exemplo 1: Listar todos os usuários

```http
GET /usuarios
```

**Resposta esperada:**

```json
[
  { "id": 1, "nome": "Alice", "email": "alice@email.com" },
  { "id": 2, "nome": "Bruno", "email": "bruno@email.com" },
  { "id": 3, "nome": "Carla", "email": "carla@email.com" }
]
```

#### Exemplo 2: Buscar um usuário específico

```http
GET /usuarios/2
```

**Resposta esperada:**

```json
{ "id": 2, "nome": "Bruno", "email": "bruno@email.com" }
```

> ⚠️ O `GET` nunca deve ter corpo na requisição. Os dados devem vir na URL ou como parâmetros de busca.

------

### 🔹 Método POST – Criação de dados

O `POST` é utilizado para **enviar dados para o servidor** e criar um novo recurso. O corpo da requisição geralmente vem em formato JSON.

#### Exemplo: Criar um novo usuário

```http
POST /usuarios
```

**Corpo da requisição:**

```json
{
  "nome": "Diego",
  "email": "diego@email.com"
}
```

**Resposta esperada:**

```json
{
  "id": 4,
  "nome": "Diego",
  "email": "diego@email.com"
}
```

> ✅ O ID geralmente é gerado automaticamente pelo servidor ou banco de dados.

Após o `POST`, o novo usuário seria adicionado ao arquivo `usuarios.json`.

------

### 🔹 Método PUT – Atualização completa de dados

O `PUT` é usado para **substituir completamente os dados de um recurso** já existente. Geralmente é enviado com todos os atributos, mesmo que apenas um tenha sido alterado.

#### Exemplo: Atualizar o usuário com ID 3

```http
PUT /usuarios/3
```

**Corpo da requisição:**

```json
{
  "nome": "Carla Mendes",
  "email": "carla.mendes@email.com"
}
```

**Resposta esperada:**

```json
{
  "id": 3,
  "nome": "Carla Mendes",
  "email": "carla.mendes@email.com"
}
```

> ⚠️ Se algum campo for omitido, o PUT poderá substituí-lo por `null`, caso a implementação não trate isso.

------

### 🔹 Método DELETE – Remoção de dados

O `DELETE` é usado para **remover um recurso** do servidor. A requisição geralmente traz o identificador do recurso na URL.

#### Exemplo: Remover o usuário com ID 2

```http
DELETE /usuarios/2
```

**Resposta esperada:**

```json
{
  "mensagem": "Usuário removido com sucesso."
}
```

Após essa requisição, o usuário Bruno deve ser removido do JSON.

> ❌ O método DELETE **não deve ter corpo**. A identificação do recurso vem diretamente na rota.

------

### 🧾 Principais Códigos de Status HTTP

Cada requisição HTTP gera uma resposta com um código de status que representa o resultado da operação. Esses códigos são divididos por categorias:

| Código | Categoria        | Significado           | Quando usar?                                |
| ------ | ---------------- | --------------------- | ------------------------------------------- |
| 200    | Sucesso          | OK                    | GET ou PUT executados com sucesso           |
| 201    | Sucesso          | Created               | POST com novo recurso criado                |
| 204    | Sucesso          | No Content            | DELETE sem corpo de resposta                |
| 400    | Erro do cliente  | Bad Request           | Dados ausentes, inválidos ou mal formatados |
| 401    | Erro do cliente  | Unauthorized          | Requisição exige autenticação               |
| 403    | Erro do cliente  | Forbidden             | Acesso negado mesmo autenticado             |
| 404    | Erro do cliente  | Not Found             | Recurso não encontrado                      |
| 500    | Erro do servidor | Internal Server Error | Erro inesperado no servidor                 |

Usar o código correto transmite clareza para o cliente e melhora a integração com outras aplicações.

------

### ✅ Conclusão do Capítulo

Neste capítulo, você:

- Aprendeu o propósito de cada método HTTP (`GET`, `POST`, `PUT`, `DELETE`);
- Viu como utilizá-los com exemplos reais baseados em um arquivo JSON local;
- Conheceu os principais códigos de status HTTP usados em APIs.

Esse conhecimento será essencial para as próximas etapas, onde criaremos nosso primeiro servidor HTTP com Node.js e implementaremos essas operações em código real.

---

### ✅ Referências

- [MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Methods)
- [Medium](https://medium.com/@renejr03/m%C3%A9todos-http-quais-s%C3%A3o-e-qual-a-funcionalidade-deles-491b1cc5d5b4)
- [DNC](https://www.escoladnc.com.br/blog/o-que-e-protocolo-http-e-metodos-de-requisicao-em-apis/)
- [FreeCodeCamp](https://www.freecodecamp.org/news/http-request-methods-explained/)
- [FreeCodeBlog](https://www.freecodecamp.org/portuguese/news/aqui-estao-as-formas-mais-populares-de-fazer-uma-solicitacao-http-em-javascript/)