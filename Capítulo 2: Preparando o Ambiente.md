## 🧠 Capítulo 2 – Preparando o Ambiente

> "Um bom código começa com um ambiente bem preparado — como um cozinheiro que organiza sua cozinha antes de começar a receita."

Antes de escrever a primeira linha de código, é essencial garantir que todo o ambiente de desenvolvimento esteja corretamente configurado. Isso evita erros desnecessários, melhora a produtividade e proporciona uma base sólida para os próximos capítulos. Neste capítulo, vamos preparar o ambiente tanto no **Windows** quanto no **Debian GNU/Linux e derivados**, utilizando ferramentas modernas para facilitar o desenvolvimento backend com Node.js e MySQL.

------

### 💻 Instalação do Node.js

O **Node.js** é a base de todo nosso backend. Ele permite executar JavaScript fora do navegador e é essencial para rodar nossos scripts e servidores.

#### 🔹 Windows

1. Acesse o site oficial: [https://nodejs.org](https://nodejs.org/)
2. Faça o download da versão LTS (Long Term Support).
3. Execute o instalador `.msi` e siga o passo a passo:
   - Aceite os termos de licença.
   - Mantenha as opções padrão.
   - Marque a opção que adiciona o Node.js ao `PATH` do sistema.

Após a instalação, abra o **Prompt de Comando** (cmd) e digite:

```bash
node -v
npm -v
```

Esses comandos devem retornar as versões instaladas do Node.js e do npm (gerenciador de pacotes).

#### 🔹 Debian GNU/Linux (e derivados)

1. Atualize o sistema:

```bash
sudo apt update && sudo apt upgrade
```

1. Instale os pacotes necessários:

```bash
sudo apt install curl -y
```

1. Baixe e execute o script oficial de instalação do Node.js:

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
```

1. Verifique as versões:

```bash
node -v
npm -v
```

> ✅ Dica: use `sudo npm install -g npm` para garantir a versão mais atual do npm.

------

### 🧰 Ferramentas úteis para o desenvolvimento

Além do Node.js, vamos utilizar ferramentas que vão **agilizar o desenvolvimento**, **facilitar o acesso ao banco de dados** e **testar nossas APIs**.

#### 🧩 Visual Studio Code (VSCode)

O **VSCode** é um dos editores de código mais populares e poderosos. Ele possui uma grande variedade de extensões, incluindo suporte a Node.js, JavaScript e integração com o terminal.

- Site oficial: [https://code.visualstudio.com](https://code.visualstudio.com/)
- Instale a versão estável para seu sistema operacional.

#### 🔌 Extensão VSCode: MySQL Client (cweijan.vscode-mysql-client2)

Essa extensão permite gerenciar bancos de dados MySQL diretamente dentro do VSCode, evitando a necessidade de ferramentas externas.

**Instalação:**

1. No VSCode, vá até a aba de extensões (ícone de quadrado à esquerda).
2. Pesquise por `MySQL` (autor: cweijan).
3. Instale a extensão `MySQL`.

**Funcionalidades principais:**

- Conectar-se a servidores MySQL locais ou remotos;
- Visualizar e editar tabelas, registros e esquemas;
- Executar comandos SQL diretamente no editor.

> 💡 Essa extensão será especialmente útil quando estivermos criando o banco de dados e testando as queries.

#### 🔍 Insomnia – Testador de Requisições HTTP

O **Insomnia** é uma ferramenta gráfica para testar APIs. Com ele, podemos simular requisições `GET`, `POST`, `PUT`, `DELETE` e visualizar os dados retornados pelo nosso servidor.

- Site oficial: [https://insomnia.rest](https://insomnia.rest/)
- Escolha a versão correspondente ao seu sistema e instale.

**Por que usar o Insomnia?**

- Interface simples e amigável;
- Permite salvar e organizar as requisições por projeto;
- Suporta autenticação, cabeçalhos personalizados, corpo da requisição em JSON, entre outros recursos avançados.

> 🧪 Testar sua API com Insomnia ajuda a validar rapidamente se o backend está funcionando como o esperado.

------

### ✅ Conclusão do Capítulo

Com o ambiente devidamente preparado, você está pronto para começar o desenvolvimento real. Ter as ferramentas corretas instaladas e configuradas é o primeiro passo para um projeto bem-sucedido. No próximo capítulo, vamos estruturar nosso projeto e iniciar o controle de versões com o `npm`. Prepare-se para colocar a mão no código!