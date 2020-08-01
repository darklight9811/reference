# Modelos

Apesar de serem chamados de modelos, eles são extendidos da sua funcionalidade no contexto geral de arquitetura de software (como por exemplo do MVC). Com modelos nos referimos a qualquer interação com banco de dados, regras de negócio, descrição, migrações e qualquer coisa a mais que tenha relação com aquele tipo de dado (usuário, produto, tags).

## Indice

Assim como dito na página de [estrutura](/pages/structure/README.md), o indice tem a função de juntar todas as partes relacionadas no modelo. Ele deve ser todo acessivel a partir do indice. O indice também tem a função de fazer a injeção de dependencias do modelo. Além de fazer as exportações separadas, é necessário juntar todos os campos em um bundle para o export padrão do arquivo.

``` typescript
export const table = "User";
export const description = "Lorem ipsum";
export const fields = [/* ... */];
// Injeção de dependencias no query builder do modelo
export const database:new Database(table, fields);

export default {
	table,
	description,
	fields,
	database,
};
```

## Dados/informações

Os dados podem ser definidos em um arquivo separado (info.ts) ou dentro do próprio indice. Neles devem conter informações que poderão ser utilizados dentro da lógica do modelo, como por exemplo:

- nome da tabela no banco
- url para requisitar na API;
- campos de migração (principalmente no caso do GraphQL, Realm DB, etc);
- relacionamentos;
- qualquer coisa que seja uma informação e não uma ação;

Atenção, se houver um arquivo info.ts, as informações terão que ser centralizadas nele.

## Indice de modelos
Uma lista contendo todos os modelos ativos da aplicação deve ser colocada num index.ts dentro da pasta `models`, dessa maneira, não precisamos excluir os links ou o próprio modelo para desativa-la do sistema, somente remover ele da lista. Um ponto único de verdade que deve ser usado de referencia para o resto da aplicação obter os modelos, nenhuma outra parte da aplicação deve acessar diretamente os modelos.

## Arquivos funcionais/efeito
### Query builder

Caso a aplicação tenha acesso direto à um banco de dados (seja interno, por conexão ou api), ele terá um arquivo query.ts. Caso exista mais um tipo de acesso ao banco, o arquivo query pode se tornar um diretório, e dentro dele um indice que retornará uma lista com todas os tipos de query builder disponiveis (cada um em seu respectivo arquivo dentro da pasta query).

### Store (context API/Redux)

Aqui serão informadas somente questões de organização de arquivo da store, caso queira ver sobre a estruturação do código para a store, procure o link [react/store](/pages/react/store.md). Store são uma maneira de unificar o fluxo de dados através da aplicação de uma maneira central (de unica verdade). A montagem da própria store não se dá dentro destes arquivos. Somente as actions, reducers e interfaces relativos somente ao modelo.

### Services

Um serviço é basicamente uma camada para a criação e gerenciamento de regras de negócio. Regras de negócio consistem de lógica para gerenciar dados, como validação, filtro e outras coisas. Services geralmente precisarão de injection do query builder. Você pode enxergar o service como o setter e o presenter como o getter.

### Presenters

Presenters são formatações para visualização do usuário, assim como o query builder, podem ser agrupados dentro de uma pasta ou dentro de somente um arquivo. Você pode enxergar o service como o setter e o presenter como o getter.

## Exemplo de modelo
```
|-- models
|	|-- user
|	|	|-- index.ts
|	|	|-- query.ts
|	|	|-- store
|	|		|-- index.ts
|	|		|-- actions.ts
|	|		|-- reducers.ts
|	|		|-- services.ts
|	|-- outro model
|-- index.ts
```