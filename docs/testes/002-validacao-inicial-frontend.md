# Validação inicial do frontend

Issue: #1.
Branch: chore/preparar-ambiente.

## Configuração

Projeto gerado com Angular CLI 22.2.7, utilizando componentes
standalone, rotas, SCSS e modo estrito, sem SSR.

## Verificações realizadas

### Compilação

Comando: npm run build

Resultado: Application bundle generation complete.

### Testes automatizados

Comando: npm test -- --watch=false

Resultado:
- 1 arquivo de testes aprovado.
- 2 testes aprovados.
- Criação do componente inicial validada.
- Renderização do título validada.

### Execução manual

Comando: npm start

Resultado: página inicial padrão acessada em http://localhost:4200.

## Alcance

As verificações validam a estrutura inicial gerada.
As funcionalidades de gestão de cursos ainda não foram implementadas.