# Estrutura de diretório

A estrutura do diretório é um dos pontos mais importantes de organização do projeto. Pois sem ela, a navegação entre códigos não irá agir de maneira humanizada, o que quer dizer. Que os usuários que irão interagir com código vão depender de mecanismos de busca para encontrar rapidamente os pontos que procuram, ao invés de pesquisarem institivamente pelos diretórios.

## Resource orientation (orientação à recursos)

Para evitar a disperção de funcionalidades destinadas à um mesmo recurso, elas devem ser coletadas no mesmo lugar, guardadas numa pasta com o nome do recurso, tendo index.ts como realmente um indice para todas as funcionalidades do recurso.

### Por que orientação à recursos?

Orientação recursos acontece quando um mesmo dado (como por exemplo usuário, publicação, comentário) está presente em vários tipos de estrutura (como query, model, presenter, service, etc). Para que você não precise ficar caçando todos as estruturas para criar um dado (e acabar esquecendo naquele lugar que você só descobre depois quando não entende por que algo está dando errado), você centraliza eles em um lugar só. Quando você tem poucos dados espalhados pelas mesmas estruturas, você pode fazer orientação à funcionalidade (functional orientation), que seria o inverso, onde o dado está espalhado pelas estruturas do projeto.

### Recursividade de dados

Existem casos onde dependencias do recurso podem ser interligadas por vias de mão dupla. Por isso, elas não podem estar presentes no mesmo. E precisam ter suas dependencias injetadas pelo indice. Seguindo o principio de inversão de dependencias do desing SOLID.

### Dados vs. lógica

Arquivos só podem ter uma função ou razão de existencia. Ele não pode conter dados e ao mesmo tempo executar regras de negócio (que podemos considerar como lógica ou serviços). Como dito na recursividade de dados, o indice terá a função de injetar as dependencias (sejam elas dados ou lógica) no arquivo quando chamado.

### Exemplo de estrutura

```
|-- componente1		// Recurso representado
|	|-- index.ts	// Faz a injeção de dependencias de outros arquivos do component
|	|-- model.ts	// Regras de negócio para interação com banco de dados
|	|-- info.ts		// Informações como nome de tabela, campos e descrição
```

## Estruturação vs. organização

Diretórios possuem duas finalidades, estruturar o tipo de arquivo dentro de si, ou organizar o mesmo tipo de estrutura. Só pode existir um tipo de diretório por contexto. Diretórios de estruturação podem ser considerados diretórios que possuem uma funcionalidade em comum, já os de organização, são meramente visuais, para melhor separação/refino dos itens no diretório.

### Explicações com md
Além do root do projeto, devem evitar adicionar arquivos md dentro das pastas. Em casos excepcionais, somente um arquivo README.md deve ser colocado. Para evitar excesso de arquivos. Já que diretórios estruturais estão sendo explicados nessa documentação, no README root do projeto, deve existir uma referencia a essa documentação para pesquisa e entendimento.

### Exemplo

```
|-- models
|	|-- general
|	|-- auth
|	|-- currency
|-- views
|	|-- front
|	|-- dash
|	|	|-- components
|	|	|-- lists
```

Como podem ver, o primeiro nivel do diretório representa uma estruturação, com modelos e views (são coisas com funções diferentes). Já o próximo nivel, no caso de modelos, é um diretório de organização, onde separamos a mesma funcionalidade em diversas pastas que apesar de ter o mesmo tipo de conteúdo, podem ser organizadas por terem muitos conteudos.