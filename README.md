# Memoteca

Aplicação web desenvolvida com Angular para registrar, listar e organizar pensamentos. O projeto disponibiliza uma interface para criar, editar, favoritar e remover post-its virtuais, além de uma API mockada com **JSON Server** responsável por persistir os dados durante o desenvolvimento.

## Sumário
- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Pré-requisitos](#pré-requisitos)
- [Como executar](#como-executar)
  - [Clonar o repositório](#1-clonar-o-repositório)
  - [Instalar dependências](#2-instalar-dependências)
  - [Iniciar o backend (JSON Server)](#3-iniciar-o-backend-json-server)
  - [Iniciar o frontend (Angular)](#4-iniciar-o-frontend-angular)
- [Estrutura de dados](#estrutura-de-dados)
- [Scripts úteis](#scripts-úteis)
- [Licença](#licença)

## Visão Geral
- **Frontend**: projeto Angular localizado em [`memoteca/`](memoteca/) com proxy configurado para consumir a API local.
- **Backend**: servidor JSON localizado em [`memoteca/backend/`](memoteca/backend/) expondo o recurso `/pensamentos` com paginação e filtros.

## Funcionalidades
- Cadastro de novos pensamentos com validações de formulário.
- Listagem paginada com botão "Carregar mais".
- Busca textual por conteúdo ou autoria.
- Edição e exclusão de pensamentos existentes.
- Marcação de favoritos e listagem dedicada "Meus Favoritos".

## Tecnologias
- [Angular 14](https://angular.io/)
- [TypeScript](https://www.typescriptlang.org/)
- [RxJS](https://rxjs.dev/)
- [JSON Server](https://github.com/typicode/json-server)
- [Node.js](https://nodejs.org/)

## Pré-requisitos
- [Node.js](https://nodejs.org/) (inclui `npm`).
- Angular CLI instalado globalmente (opcional, mas recomendado): `npm install -g @angular/cli`.

## Como executar

### 1. Clonar o repositório
```bash
git clone https://github.com/gsoaresdz/memoteca.git
cd memoteca
```

### 2. Instalar dependências
Instale as dependências do frontend e, em seguida, do backend mockado:
```bash
cd memoteca      # entra no projeto Angular
npm install      # instala as dependências do frontend
cd backend
npm install      # instala as dependências do JSON Server
```

> Observação: mantenha dois terminais ou utilize processos em segundo plano para executar frontend e backend simultaneamente.

### 3. Iniciar o backend (JSON Server)
Dentro de `memoteca/backend/` execute:
```bash
npm start
```
O servidor será iniciado em `http://localhost:3000` com o endpoint `/pensamentos` definido em [`db.json`](memoteca/backend/db.json).

### 4. Iniciar o frontend (Angular)
Em outro terminal (ou após voltar da pasta `backend` com `cd ..`), dentro de `memoteca/` execute:
```bash
npm start
```
O comando utiliza o `ng serve` com o proxy [`proxy.conf.json`](memoteca/proxy.conf.json). A aplicação ficará disponível em `http://localhost:4200/`.

## Estrutura de dados
Cada pensamento possui os seguintes campos:
| Campo     | Tipo     | Descrição                         |
|-----------|----------|-----------------------------------|
| `id`      | `number` | Identificador gerado pelo JSON Server.
| `conteudo`| `string` | Texto principal do pensamento.
| `autoria` | `string` | Autor do pensamento.
| `modelo`  | `string` | Variante visual do card (ex.: `modelo1`).
| `favorito`| `boolean`| Indica se o pensamento está favoritado.

## Scripts úteis
No diretório `memoteca/`:
- `npm start`: executa o servidor de desenvolvimento com proxy configurado.
- `npm run build`: gera a build de produção em `dist/`.
- `npm test`: executa os testes unitários via Karma.

No diretório `memoteca/backend/`:
- `npm start`: inicia o JSON Server observando `db.json`.

## Licença
Este projeto está licenciado sob a [MIT License](LICENSE).

---
Feito com :heart: por [gsoaresdz](https://github.com/gsoaresdz)
