<center>

[🏠 Home](../index.md)

</center>

#

<h1 align="center">Union Types e Type Alias</h1>

> Union types são utilizados quando um valor pode ser mais de um tipo.
> Fonte: https://www.typescriptlang.org/docs/handbook/unions-and-intersections.html

Para entender melhor o conceieto, imaginemos o seguinte cenário:
Dada a necessidade de criar uma função que que adicione preenchimento a esquerda,
vamos criar a nossa primeira versao da função

```typescript
/**
 * Pega uma string e adiciona "preenchimento" à esquerda.
 * Se 'padding' for uma string, 'padding' será anexado ao lado esquerdo.
 * Se 'preenchimento' for um número, esse número de espaços será adicionado ao lado esquerdo.
 */
function padLeft(value: string, padding: any) {
  if (typeof padding === "number") {
    return " ".repeat(padding) + value;
  }
  if (typeof padding === "string") {
    return padding + value;
  }
  throw new Error(`Expected string or number, got '${typeof padding}'.`);
}
```

Nossa função só deve trabalhar com os tipos string e numero.

```typescript
console.log(padLeft("Texto", 5));
console.log(padLeft("Texto", "aa"));
console.log(padLeft("Texto", true));
```

Porem usar o tipo any, apesar da documentação da função dizer
que só deve receber string e nuber, algum progrador desatento pode estar passando como paramentro um boolean por exemplo, e o TS não dara nenhum
aviso na hora de compilação, sómente no momento de execução que o JS ira retornar o erro. Então como podemos evitar isso?

Podemos atualizar nossa função para utilizar Union Types.

```typescript
function padLeft(value: string, padding: string | number) {
  if (typeof padding === "number") {
    return " ".repeat(padding) + value;
  }
  return padding + value;
}
```

Usando Union Types o Transpilador nos avisa que algo está errado no nosso código.

```typescript
console.log(padLeft("Texto", 5));
console.log(padLeft("Texto", "aa"));
console.log(padLeft("Texto", true)); //O que acontece nesta linha?
```

Caso esse tipo de retrição venha se repetir em outras partes do nosso código, podemos também criar um **Type Alias** para ele.

```typescript
type Padding = string | number;
function padLeft(value: string, padding: Padding) {
  if (typeof padding === "number") {
    return " ".repeat(padding) + value;
  }
  return padding + value;
}
console.log(padLeft("Texto", "aa"));
console.log(padLeft("Texto", 10));
```

#

<center>

[🏠 Home](../index.md)

</center>
