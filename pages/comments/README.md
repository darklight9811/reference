# Comentários

Comentários são de extrema importancia. Podemos separa-los em três tipos principais: comentários funcionais (os mais comuns que você encontra na maioria dos locais), os comentários seccionais e comentários jsdoc.

## Comentários funcionais

São comentários que tem o intuito de explicar a funcionalidade ou conteúdo do código em seguida, marcar peculiaridades (maneiras que parecem erradas mas são a maneira que o código funciona), mostrar intenção de correção futura, ou qualquer outra descrição. Comentários devem evitar ficar na mesma linha que o código, sempre precedendo eles.

### Exemplos de comentários funcionais

``` javascript
// TODO recuperar dados da api
const results = [];

// Pega as informações do usuário logado no sistema
const results = api.get('userService');
```

## Comentários seccionais

Comentários seccionais são mais importantes do que seu próprio conteúdo, o que isso quer dizer? Eles servem de marcação para formatação do código. Como uma borda, heading ou separação. Eles podem conter um conteúdo funcional (juntando o comentário seccional com o funcional). Mas caso não seja funcional, você pode perceber que não tem muita utilidade ler ele, apenas de perceber sua existencia.

### Exemplo de comentários seccionais

``` javascript
//------------------------
// Métodos
//------------------------
```

O comentário acima tem a finalidade de separar em seções uma classe, por exemplo, a seção de variaveis (propriedades/atributos), dos métodos.

## Comentários jsdoc

São um tipo de comentário bem fundamentado na comunidade javascript e PHP. Para uma documentação mais aprofundada sobre eles, acesse esse [link](https://jsdoc.app/). São necessarios em todos os métodos/funções não encapsuladas (funções públicas) que são exportadas do arquivo. Eles são de extrema importancia, por serem captadas pela IDE para servirem de guia para qualquer pessoa que queira utilizar a função.

### Exemplo de comentários jsdoc

``` typescript
/**
 * Get
 *
 * @description Recovers a value from the dictionary 
 * @param {string} key The key that identifies the value you are searching for
 * @param {any} default The default value to be returned in case the key is not found
 * @returns {any} Value to be returned based on the dictionary
 */
public get (key : string, default? : any) : any  {
	return this.dictionary[key] ? this.dictionary[key]:default;
}
```