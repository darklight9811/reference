# Componentes

Componentes são classes ou funções que renderizam algo para o usuário. Diferente da convenção geral, não chamamos componentes de dumb e smart, aqui os componentes são equivalentes ao dumb components e os módulos ao smart components. Voltando aos componentes, eles não são proibidos de possuir estado interno, mas esse estado não pode possuir nenhum efeito na estrutura de dados do sistema, como salvar informações. Todos os componentes descritos aqui devem seguir a regra [pasta-componente](/pages/structure/general.md).

## Componentes recorrentes

Muitas vezes temos componentes que são recorrentes na maioria dos tipos de projeto, como um input, select, form. Preferencialmente seria correto iniciar um repositório para criação de uma lib somente para eles (recomendamos [create-react-library](https://www.npmjs.com/package/create-react-library), é muito bom, sério), mas as vezes pelo tamanho do projeto é algo inviavel.

### Por que separar o projeto de seus componentes visuais recorrentes?

Apesar de utilizarmos o git para versionamento e suas branches para cada membro da equipe, muitas vezes uma má ação de qualquer membro, ou muitos membros pode causar confusão no projeto. Separar ele em dois repositórios diferentes e consequentemente em uma library, ajuda a segregar os membros para que um não possa atrapalhar o trabalho do outro. Sem contar uma pipeline mais refinada para capturar erros e corrigir código.

## Componentes dedicados

Componentes dedicados são componentes não recorrentes dentro do contexto do mesmo projeto. Por exemplo, um item de uma lista que aparecerá em apenas uma página. Eles devem ser separados em uma pasta com o intuito especifico de armazenar somente estes componentes (damos o nome geralmente de shared ou componentes), eles podem estar presentes dentro do contexto de outro componente ou de uma view. Mesmo sendo algo de porte menor, eles não podem estar presentes num mesmo arquivo ou fugir da regra [pasta-componente](/pages/structure/general.md).

## Componentes gerais

