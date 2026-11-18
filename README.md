# Gestão de Cursos

Projeto de estudo baseado no desafio US030 — Manter Cursos, realizado
durante uma turma de formação da Cast.

## Objetivo

Permitir que um administrador cadastre, consulte, altere e exclua cursos,
respeitando regras de período, duplicidade e auditoria.

## Tecnologias definidas

- Front-end: Angular e TypeScript.
- Back-end: Java 17 e Spring Boot.
- Banco de dados: PostgreSQL.
- Ambiente local: Docker Compose.

As versões dos frameworks serão registradas nas decisões técnicas.

## Organização

- backend/: API, a ser criada.
- frontend/: aplicação web, a ser criada.
- docs/requisitos/: requisitos e regras aprovadas.
- docs/decisoes/: decisões técnicas.
- docs/testes/: evidências de testes.

## Desenvolvimento

Cada implementação será organizada em issue, branch e pull request,
com testes relevantes e revisão antes da integração.

## Situação atual

Backend e frontend gerados e validados localmente.
Build e testes automatizados configurados no GitHub Actions.
Funcionalidades de cursos ainda não implementadas.

A execução será local, sem publicação em produção.

## Documentação

- [Requisitos aprovados](docs/requisitos/US030-manter-cursos.md)

## Pré-requisitos

- JDK 17.
- Node.js 24.22.2 e npm.
- Docker Engine e Docker Compose.

O Maven é executado pelo Wrapper incluído no backend.

## Preparar o ambiente local

Na raiz do repositório, crie a configuração local:

```bash
cp -n .env.example .env
docker compose up -d --wait
```

O PostgreSQL fica disponível em localhost:5434.
O arquivo .env não deve ser versionado.

## Executar o backend

Em um terminal Bash, na raiz do repositório:

```bash
set -a
source .env
set +a

cd backend
./mvnw spring-boot:run
```

A API utiliza http://localhost:8080.
Ainda não existem endpoints de negócio.

## Executar o frontend

Em outro terminal, na raiz do repositório:

```bash
cd frontend
npm ci
npm start
```

Acesse http://localhost:4200.

## Executar os testes

Backend, com o banco iniciado e as variáveis carregadas:

```bash
cd backend
./mvnw clean verify
```

Frontend, dentro da pasta frontend:

```bash
npm test -- --watch=false
npm run build
```

## Encerrar a execução

Use Ctrl+C nos terminais do backend e do frontend.

Na raiz do repositório, pare o banco:

```bash
docker compose stop
```

Os dados permanecem no volume do Docker.

## Integração contínua

O GitHub Actions executa build e testes do backend e do frontend.
O backend utiliza um PostgreSQL temporário, separado do banco local.
O workflow não realiza deploy.
