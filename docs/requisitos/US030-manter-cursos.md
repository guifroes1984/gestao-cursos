# US030 — Manter Cursos

Status: refinamento aprovado.

## História de usuário

Como administrador, quero gerenciar os cursos disponíveis da Cast.

## Origem e escopo

Baseado no documento US030 — Manter Cursos da turma de formação.
As definições complementares abaixo foram aprovadas durante o refinamento.

## Funcionalidades

- Acessar a funcionalidade pelo menu principal "Curso".
- Cadastrar, listar, visualizar, alterar e excluir cursos.
- Pesquisar pelo nome e pelo período.
- Disponibilizar os botões "Adicionar" e "Voltar".
- Apresentar mensagens de validação e confirmação de gravação.

## Campos

- Descrição do assunto: obrigatória.
- Data de início: obrigatória.
- Data de término: obrigatória.
- Quantidade de alunos por turma: opcional; inteiro maior que zero.
- Categoria: obrigatória; selecionada entre as categorias do banco.

## Categorias iniciais

- Multiplataforma.
- Banco de dados.
- Metodologia.
- Comportamento.
- Comunicação.

## Regras aprovadas

### RN01 — Períodos

Não permitir cursos com qualquer dia em comum, independentemente da
categoria. As datas inicial e final fazem parte do período.

Se um curso termina em 20/11, outro pode começar a partir de 21/11.

Mensagem obrigatória para conflito:
"Existe(m) curso(s) planejados(s) dentro do período informado."

A API deve retornar um código de erro, a definir no contrato técnico.

### RN02 — Validação das datas

- Permitir início na data atual.
- Impedir cadastro com início anterior à data atual.
- Impedir término anterior ao início.
- Permitir início e término no mesmo dia.

### RN03 — Alteração

- Validar conflitos desconsiderando o próprio curso.
- Permitir editar outros campos de cursos iniciados, mantendo a data
  original de início.
- Se a data de início for alterada, não permitir uma nova data no passado.
- Aplicar as demais validações de cadastro.

### RN04 — Duplicidade

Considerar duplicado o curso cuja descrição seja igual à de outro curso,
desconsiderando maiúsculas, minúsculas e espaços nas extremidades.

Na alteração, desconsiderar o próprio curso na verificação.

### RN05 — Exclusão

Permitir a exclusão somente antes da data de início.
Bloquear cursos em andamento ou encerrados.

### RN06 — Pesquisa

Permitir pesquisa por nome e período.

Na pesquisa por período, retornar cursos que compartilhem pelo menos
um dia com o intervalo informado.

### RN07 — Identificação do responsável

Utilizar inicialmente um administrador identificado pela aplicação,
sem implementar um módulo de login.

Essa identificação não representa autenticação de usuário.

### RN08 — Auditoria

Registrar cada inclusão e alteração em tabela de log, contendo:

- Identificação do curso.
- Operação realizada.
- Data e hora.
- Usuário responsável.

Manter o histórico de inclusão e das atualizações.

## Cenários essenciais de aceite

1. Um cadastro válido grava o curso e seu log e apresenta confirmação.
2. A ausência de um campo obrigatório impede a gravação e apresenta alerta.
3. Início anterior à data atual impede o cadastro.
4. Término anterior ao início impede a gravação.
5. Um curso de um único dia pode ser cadastrado.
6. Sobreposição parcial, total ou em uma extremidade impede a gravação.
7. Descrição duplicada impede a gravação e apresenta alerta.
8. A alteração sem mudança de período não conflita com o próprio curso.
9. A alteração registra uma nova entrada de log.
10. Curso iniciado ou encerrado não pode ser excluído.
11. Curso futuro pode ser excluído.
12. A pesquisa por período retorna cursos parcialmente abrangidos.
13. Quantidade de alunos em branco é aceita; zero, negativos e frações
    são rejeitados.

Os cenários de datas devem utilizar uma data de referência controlada
nos testes.

## Entregáveis do enunciado

- Código-fonte versionado no GitHub.
- Scripts de banco de dados.
- Evidências de testes.
- Descrição técnica da solução.

## Fora do escopo inicial

- Publicação em produção.
- Módulo de login.
- Cadastro de alunos e matrículas.
- Gerenciamento de categorias pela interface.
