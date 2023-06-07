<center>

[🏠 Home](../index.md)

</center>

#

<h1 align="center">Array</h1>

> Um array (arranjo ou vetor) é um conjunto de dados (que pode assumir os mais diversos tipos, desde do tipo primitivo, a objeto dependendo da linguagem de programação). Arrays são utilizados para armazenar mais de um valor em uma única variável. Isso é comparável a uma variável que pode armazenar apenas um valor.
> Cada item do array tem um número ligado a ele, chamado de índice numérico, que permite acesso a cada "valor" armazenado na váriavel.
> Em JavaScript, um array começa no índice zero e pode ser manipulado a partir de vários métodos (en-US).
> fonte:https://developer.mozilla.org/pt-BR/docs/Glossary/Array

Vale ressaltar que é possível armazenar varios tipos primitivos em uma unica Array, porém você não obeterá a vantagem do sistema de tipos do Typescript.

Modo mais utilizado de declarar uma array:

```typescript
// escopoVariavel nomeVariavel: tipoVariavel[] = [valor1, valor2, valor3]

let nomes: string[] = ["abgail", "bento", "claudio"];
console.log(nomes); //saída ["abgail", "bento", "claudio"]
```

Outro modo de declarar uma array:

```typescript
// escopoVariavel nomeVariavel: Array<tipoVariavel> = [valor1, valor2, valor3]

let notas: Array<number> = [10, 9.5, 10];
console.log(notas); //saída [10, 9.5, 10]
```

Para acessar os dados de uma Array utilizamos a seguinte sintaxe, **nomeVariavel[index]**, sendo index a posição do objeto na Array,e que a posição inicial é 0.

```typescript
// nomeVariavel[index]
console.log("Acessando no index 0: ");
console.log(nomes[0]);
console.log(notas[0]);
console.log("Acessando no index 1: ");
console.log(nomes[1]);
console.log(notas[1]);
```

```typescript
console.log(typeof nomes); //saída object
console.log(typeof nomes[0]); //saída string
console.log(typeof notas[0]); //saída number
```

Para inserir dados em uma array podemos utilizar o método **push**.

```typescript
nomes.push("Donatelo");
console.log(nomes); //saída ["abgail", "bento", "claudio", "Donatelo"]
```

Podemos remover um item de uma array podemos utilizar o método **slice**. No primeiro parâmetro função recebe a posição do item, e no segundo a quantidade de itens a ser removida.

```typescript
nomes.splice(0, 1);
console.log(nomes); //saída ["bento", "claudio", "Donatelo"
```

Para consultarmos o tamanho da nossa Array, podemos utilizar a propriedade leght

```typescript
const capitaes = ["Picard", "Kirk", "Janeway", "pike"];

console.log(capitaes.length); // saída 4
```

<h2 align="center"> 
	🎲 Hands on 002 🎲
</h2>

1. Crie um array do tipo texto vazia e em seguida adicione o nome dos participantes do seu grupo e exiba no console.

2. Crie um array com o nome de todas as disciplinas cursadas no semestre no momento da declaração da array.

3. Exiba no console o nome da disciplina e o nome do aluno do grupo que obtem melhor desempenho na mesma.

4. Exiba no console a resposta para a pergunta: O que acontece se passamos o segundo parâmetro o valor 0, na função splice.

#

<center>

[🏠 Home](../index.md)

</center>
