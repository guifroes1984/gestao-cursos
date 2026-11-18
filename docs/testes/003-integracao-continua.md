# Validação da integração contínua

Data: 18/11/2026.
Issue: #1.
Pull request: #2.

## Configuração

Workflow: .github/workflows/ci.yml.

- Backend: Java 17, PostgreSQL temporário e Maven clean verify.
- Frontend: Node 24, npm ci, build e testes.
- Sem etapas de deploy.

## Resultado observado

As execuções disparadas pelo push e pela atualização do pull request
foram concluídas com sucesso no GitHub Actions.

## Referência

https://github.com/guifroes1984/gestao-cursos/actions