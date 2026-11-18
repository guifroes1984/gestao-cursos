# ADR 001 — Base técnica

Status: aceita.
Data: 2026-11-17.
Issue: #1.

## Contexto

Implementar o desafio US030 — Manter Cursos com execução local,
testes automatizados e versionamento no GitHub, sem deploy.

## Decisões

- Backend: Java 17 e Spring Boot 4.1.2.
- Build: Maven Wrapper versionado no repositório.
- API REST com DTOs separados das entidades.
- Organização do backend por funcionalidade.
- Persistência com Spring Data JPA e PostgreSQL 17.
- Banco local executado com Docker Compose.
- Porta local do banco: 5434; porta interna: 5432.
- Alterações do banco controladas pelo Flyway.
- Hibernate configurado com ddl-auto=validate.
- Open Session in View desabilitado.
- Configurações externas fornecidas por variáveis de ambiente.
- DevTools utilizado no desenvolvimento local.
- Frontend em Angular e TypeScript; versão ainda a definir.
- Código de negócio em português.
- Testes unitários para regras e testes de integração para persistência.
- Entregas por issue, branch e pull request.
- Integração contínua sem deploy, ainda a configurar.

## Consequências

- O banco precisa estar disponível para o teste de contexto atual.
- Executar pelo terminal exige carregar as variáveis de ambiente.
- Mudanças no esquema serão feitas por migrations, sem atualização
  automática de tabelas pelo Hibernate.
- Os testes de integração deverão utilizar banco isolado antes de
  implementarmos operações que alterem dados.
- Configurações específicas do VS Code permanecem locais.

## Referências

- https://docs.spring.io/spring-boot/
- https://maven.apache.org/wrapper/
- https://docs.docker.com/compose/
