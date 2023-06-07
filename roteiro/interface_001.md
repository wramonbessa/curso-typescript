<center>

[🏠 Home](../index.md)

</center>

#

<h1 align="center">Interface</h1>

> Um dos princípios básicos do TypeScript é que a verificação de tipo se concentra na forma que os valores têm. Isso às vezes é chamado “subtipagem estrutural”. No TypeScript, as interfaces preenchem o papel de nomear esses tipos e são uma maneira poderosa de definir contratos dentro do seu código, bem como contratos com código fora do seu projeto. fonte: https://www.typescriptlang.org/docs/handbook/interfaces.html

### Declaração

Utilizamos a seguinte estrutura para definir uma interface:

```typescript
interface Estudante {
  nome: string;
  nota: number;
}
```

Para utilizar basta criarmos nossa variável informando o tipo

```typescript
const estudante1: Estudante = { nome: "Abgail", nota: 10 };
console.log(estudante1);
console.log(typeof estudante1);
```

O que acontece se tentarmos criar um Aluno sem um dos atributos?

```typescript
let aluno2: Aluno = { nome: "Bento" };
```

Para criarmos interfaces com atributos opcionais podemos utilizar o modificador ?

```typescript
interface Professor {
  nome: string;
  formacao: string;
  idade?: number;
}
const professor1: Professor = {
  nome: "Bento",
  formacao: "Licenciatura em Informática",
};
const professor2: Professor = {
  nome: "Carlos",
  formacao: "Sistemas de Informação",
  idade: 10,
};
console.log(professor1);
console.log(professor2);
```

<h2 align="center"> 
	🎲 Hands on 004 🎲
</h2>

As respostas para as perguntas a seguir devem ser de acordo com o contexto do seu projeto.

1. Crie uma função chamda getProdutos, a função deve retornar um array do tipo Produto. A interface do tipo produto deve ter um nome, preco e descricao.

1. Crie uma função chamda maior getLengthProdutos, ela deve receber uma array do Produto (retorno da funcao getProdutos) e deve retornar a quantidade de produtos cadastrados. Exibir retorno no console.

1. Crie uma função chamda exibeProdutos, ela deve receber uma array de Produtos (retorno da funcao getProdutos) e exibir no console o nome, descricao e valor de todos os produtos.

1. Crie uma função chamda getProdutosMaiorValor, ela deve receber uma array de Produtos (retorno da funcao getProdutos) e retornar os objeto com maior valor. Com o retorno da função, exibir nome, valor e descrição do produto(s) retornado(s).

1. Crie uma função chamda getProdutosMenorValor, ela deve receber uma array de Produtos (retorno da funcao getProdutos) e retornar os objetos com menor valor. Com o retorno da função, exibir nome, valor e descrição do(s) produto(s) retornado.

1. Crie uma função chamda maior getPrecoMedio, ela deve receber uma array do Produto (retorno da funcao getProdutos) e retornar o valor do preco medio dos produtos. Com o retorno da função, exibir nome, valor e descrição do produto retornado.

1. Crie uma função chamda maior getQtdAcimaMedia, ela deve receber uma array do Produto (retorno da funcao getProdutos) e utilizando a funcao getPrecoMedio retornar a quantidade de produtos que estão igual ou acima do valor médio. Com o retorno da função, exibir uma mensagem no console.

1. Crie uma função chamda maior getQtdAbaixoMedia, ela deve receber uma array do Produto (retorno da funcao getProdutos) e utilizando a funcao getPrecoMedio retornar a quantidade de produtos que abaixo do valor médio. Com o retorno da função, exibir uma mensagem no console.

1. Crie uma função chamda maior getProdutosAcimaMedia, ela deve receber uma array do Produto (retorno da funcao getProdutos) e utilizando a funcao getPrecoMedio retornar os objetos que estão igual ou acima do valor médio. Com o retorno da função, exibir nome, valor e descrição do produto retornado.

1. Crie uma função chamda maior getProdutoAbaixoMedia, ela deve receber uma array do Produto (retorno da funcao getProdutos) e utilizando a funcao getPrecoMedio retornar os objetos que estão abaixo do valor médio. Com o retorno da função, exibir nome, valor e descrição dos produtos retornados.

#

<center>

[🏠 Home](../index.md)

</center>
