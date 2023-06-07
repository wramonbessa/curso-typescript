<center>

[🏠 Home](../index.md)

</center>

#

<h1 align="center">Utilizando Props</h1>

## O que são as props?

> Os componentes do React usam props para se comunicarem uns com os outros. Cada componente pai pode passar algumas informações para seus componentes filhos, dando-lhes props. Podendo ser passado qualquer valor JavaScript por meio deles, incluindo objetos, arrays e funções.
> Fonte: https://react.dev/learn/passing-props-to-a-component

Crie um arquivo chamado ListagemV1.tsx, e execute o comando **tsrfce**. Esse componente vai servir como uma listagem padrão de itens, que pode vim a ser utilizada em varios locais do nosso site. Primeiro vamos adicionar um título para nossa listagem confome o código a seguir:

```typescript
import React from "react";
type Props = {
  titulo: string;
};
function ListagemV1({ titulo }: Props) {
  return (
    <div>
      <h2>{titulo}</h2>
    </div>
  );
}
export default ListagemV1;
```

Para passar parâmetros para o componente é preciso inserir na Props e atualizar na chamada da função, só assim o menos vai poder ser utilizado na função. Vale ressaltar que na Props, podemos declarar nossas propriedades de forma tipada.

Para utilizar esse componente basta atualizarmos nosso arquio App.tsx, e ao utilizarmos nosso componente ListagemV1 passarmos a propriedade título.

```typescript
import React from "react";
import ListagemV1 from "./components/ListagemV1";
function App() {
  return (
    <div className="App">
      <ListagemV1 titulo="Serviços" />
    </div>
  );
}
export default App;
```

Agora vamos atualizar nossa lista para receber os seus itens. Primeiro inserimos dentro do type props nossa array de itens do tipo string. Em seguida criamos nossa listagem utilizando a tag **ol** e utilizamos o laço map para exibir nossos itens.

```typescript
import React from "react";
type Props = {
  titulo: string;
  itens: string[];
};
function ListagemV1({ titulo, itens }: Props) {
  return (
    <div>
      <h2>{titulo}</h2>
      <ol>
        {itens.map((item) => (
          <li>{item}</li>
        ))}
      </ol>
    </div>
  );
}
export default ListagemV1;
```

Agora atualizamos o arquivo App.tsx, para passar os itens.

```typescript
import React from "react";
import ListagemV1 from "./components/ListagemV1";
function App() {
  return (
    <div className="App">
      <ListagemV1 titulo="Serviços" itens={["Serviço 1", "Serviço 2"]} />
    </div>
  );
}
export default App;
```

Na tag

<h2 align="center"> 
	🎲 Hands on R003 🎲
</h2>

1. No seu site atualize para que a listagem de serviços/produtos use um componente usando props, adicione também um parâmetro de valor.

1. Crie um componente de Noticia, nele deve ter título, autor, texto, tags(lista de assuntos) e data de criação.

1. Use sua criatividade e crie um componente passando uma propriedade.

1. **EXTRA** Atualize a sua listagem para que o objeto do tipo item tenha origem de uma interface.

<center>

[🏠 Home](../index.md)

</center>
