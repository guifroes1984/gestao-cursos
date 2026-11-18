# Validação da migration inicial

Data: 18/11/2026.
Issue: #1.
Branch: chore/preparar-ambiente.

## Objetivo

Validar a aplicação da primeira migration em um banco vazio,
separado do banco local de desenvolvimento.

## Ambiente

- PostgreSQL 17 em Docker.
- Banco: gestao_cursos_validacao.
- Migration: V1__criar_tabela_categoria.sql.

## Procedimento

1. Criar o banco vazio gestao_cursos_validacao.
2. Carregar as variáveis locais de ambiente.
3. Executar no diretório backend:

POSTGRES_DB=gestao_cursos_validacao ./mvnw --batch-mode --no-transfer-progress clean verify

4. Consultar flyway_schema_history e a estrutura de TBL_CATEGORIA.

## Resultados

- Build concluído com BUILD SUCCESS.
- Flyway registrou a versão 1 com success = true.
- Tabela TBL_CATEGORIA criada.
- Coluna id com geração automática e chave primária.
- Coluna nome obrigatória, limitada a 100 caracteres.
- Restrições de unicidade e nome não vazio presentes.

## Alcance

Validada a aplicação da migration e a existência das restrições.
A rejeição de dados inválidos ainda não foi testada.