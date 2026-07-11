# Cypress Intermediário - Testes Automatizados

Projeto de testes automatizados desenvolvido durante o curso **Testes Automatizados com Cypress (Intermediário)** da [Escola TAT](https://www.udemy.com/user/walmyr/).

## Sobre o projeto

Testes automatizados de uma aplicação GitLab CE rodando localmente via Docker, cobrindo funcionalidades como login, logout e criação de projetos.

## Tecnologias utilizadas

- [Cypress](https://www.cypress.io/) `v12.0.2`
- [@faker-js/faker](https://fakerjs.dev/) `v7.6.0`
- [cypress-plugin-api](https://github.com/filiphric/cypress-plugin-api) `v2.6.1`
- [Docker](https://www.docker.com/)
- [GitLab CE](https://gitlab.com/gitlab-org/gitlab-foss) `v12.5.2`

## Pré-requisitos

- [Node.js](https://nodejs.org/) (versão LTS)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com/)

## Configuração do ambiente

### 1. Suba o GitLab com Docker

```bash
docker run --publish 80:80 --publish 22:22 --hostname localhost wlsf82/gitlab-ce
```

Aguarde alguns minutos até o GitLab inicializar. Acesse `http://localhost` e defina a senha do usuário `root`.

### 2. Clone o repositório

```bash
git clone https://github.com/nathalyamarianosilva-ship-it/cypress-intermediario.git
cd cypress-intermediario
```

### 3. Instale as dependências

```bash
npm install
```

### 4. Configure as variáveis de ambiente

Copie o arquivo de exemplo e preencha com suas credenciais:

```bash
cp cypress.env.json.example cypress.env.json
```

Edite o `cypress.env.json` com seus dados:

```json
{
  "user_name": "root",
  "user_password": "sua-senha",
  "gitlab_access_token": "seu-access-token"
}
```

## Executando os testes

### Modo headless (linha de comando)

```bash
# Todos os testes
npx cypress run

# Teste específico
npx cypress run --spec "cypress/e2e/gui/login.cy.js"
npx cypress run --spec "cypress/e2e/gui/logout.cy.js"
npx cypress run --spec "cypress/e2e/gui/createProject.cy.js"
```

### Modo interativo

```bash
npx cypress open
```

## Estrutura do projeto

```
cypress/
├── e2e/
│   └── gui/
│       ├── login.cy.js          # Testa o login via GUI
│       ├── logout.cy.js         # Testa o logout via GUI
│       └── createProject.cy.js  # Testa a criação de projeto via GUI
├── support/
│   ├── e2e.js                   # Arquivo de suporte principal
│   └── gui_commands.js          # Comandos customizados do Cypress
└── downloads/                   # Pasta para downloads dos testes
cypress.config.js                # Configurações do Cypress
cypress.env.json.example         # Exemplo de variáveis de ambiente
```

## Funcionalidades testadas

| Funcionalidade | Tipo | Arquivo |
|---|---|---|
| Login | GUI | `login.cy.js` |
| Logout | GUI | `logout.cy.js` |
| Criação de projeto | GUI | `createProject.cy.js` |

## Boas práticas aplicadas

- **`cy.session()`** para cachear e reutilizar sessão entre testes
- **Validação de sessão** para garantir independência entre testes
- **Dados dinâmicos** com `faker.js` para evitar conflitos
- **Comandos customizados** para reuso de código
- **Variáveis de ambiente** para proteger dados sensíveis

---

Desenvolvido por [Nathalya Mariano](https://github.com/nathalyamarianosilva-ship-it)
