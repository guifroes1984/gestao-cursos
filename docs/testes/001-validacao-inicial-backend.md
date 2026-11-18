# Validação inicial do backend

Data: 17/11/2026.
Issue: #1.
Branch: chore/preparar-ambiente.

## Ambiente

- Java 17.
- Spring Boot 4.1.2.
- PostgreSQL 17 em Docker, na porta local 5434.

## Execução

Com o banco iniciado e as variáveis de ambiente carregadas,
foi executado no diretório backend:

./mvnw -U clean verify

## Resultado

- BUILD SUCCESS.
- Testes executados: 1.
- Falhas: 0.
- Erros: 0.
- Ignorados: 0.
- Tempo do teste: 88,14 segundos.
- Classe: com.gestaocursos.backend.BackendApplicationTests.

## O que foi validado

O teste inicial confirmou o carregamento do contexto Spring.
A execução manual também confirmou a conexão com o PostgreSQL
e a inicialização do Flyway.

As regras de negócio dos cursos ainda não foram implementadas
nem testadas.