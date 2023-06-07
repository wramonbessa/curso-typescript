<center>

[🏠 Home](../index.md)

</center>

#

<h1 align="center">Hooks State</h1>

## O que é Hooks?

> Traduzindo para o português, “Hooks” significa ganchos. Esses hooks foram introduzidos no React a partir da versão 16.8 da biblioteca, sendo recursos que permitem que você gerencie o estado, ciclos de vida do componente e outros recursos do React sem precisar escrever componentes em forma de classes.

> Fonte: https://blog.betrybe.com/tecnologia/react-hooks/#1

Crie um arquivo arquivo chamado Hook.tsx, e execute o comando **tsrfce**. Esse componente vai servir como exemplo do nosso primeiro hook, note que para esse primeiro exemplo não vamos fazer uso de props. Definimos o estado padrão de carregamento por meio do **useState** Altere seu código conforme o exemplo a seguir:

```typescript
import React, { useState } from "react";
function State() {
  const [text, setText] = useState("texto inicial");
  return (
    <div>
      <p>Texto state: {text}</p>
    </div>
  );
}
export default State;
```

Agora vamos atualizar nosso arquivo App.tsx.

```typescript
import React from "react";

import State from "./hook/State";
function App() {
  return (
    <div className="App">
      <State />
    </div>
  );
}
export default App;
```

Desse modo temos definido o valor padrão de carregamento do nosso text. Porém o grande benefício do hooks é fazer a atualização do estado do nosso componente, para fazer isso vamos atualizar nosso arquivo **Hook.tsx**. Primeiramente, vamos adicionar um input, para que toda vez que ele for alterado, o nossa variável seja atualizada.

Para fazer isso vamos utilizar onChage do input e criar a função que deve ser chamada a **handleChange**. Agora toda vez que o valor do input for alterado, é executada a função handleChange e nela é chamado a função **setText** que atualiza o estado da nossa variável. Conforme o código a seguir:

```typescript
import React, { useState, ChangeEvent } from "react";
function State() {
  const [text, setText] = useState<string | null>(null);
  const handleChange = (e: ChangeEvent<HTMLInputElement>) => {
    setText(e.target.value);
  };
  return (
    <div>
      <p>Texto state: {text}</p>
      <input type="text" onChange={handleChange} />
    </div>
  );
}
export default State;
```

Nesse exemplo utilizamos hooks state para fazer o controle de um valor textual. Más podemos também fazer para valor numericos, como por exemplo um contador de cliques, conforme o código a seguir.

```typescript
import React, { useState, ChangeEvent } from "react";
function State() {
  const [text, setText] = useState<string | null>(null);
  const handleChange = (e: ChangeEvent<HTMLInputElement>) => {
    setText(e.target.value);
  };
  //Exemplo contador
  const [count, setCount] = useState(0);
  const handleChangeCount = () => {
    setCount(count + 1);
    //setCount(count+ 1)
  };
  return (
    <div>
      <p>Texto state: {text}</p>
      <input type="text" onChange={handleChange} />
      <p>Você clicou {count} vezes</p>
      <button onClick={handleChangeCount}>Clique aqui</button>
    </div>
  );
}
export default State;
```

Ao fazer alteração do valor passando diretamente a referência do hook pode acarretar em um comportamento inesperado se por exemplo descomentarmos o código presente na função **handleChangeCount**. O que acontece? o incremento não é realizado duas vezes pois a função **setCount** é rodado de forma assincrona, logo não se tem a refência de valor. Para alterarmos o valor de forma conciente precisamos usar o previous value. Conforme a atualiação da função **handleChangeCount** a seguir, onde por meio de uma array function passamos como parâmetro o valor previo e como ele deve ser trabalhado.

```typescript
const handleChangeCountPlus = () => {
  setCount((prevCount) => prevCount + 1);
  setCount((prevCount) => prevCount + 1);
};
```

> Referências:
>
> https://blog.logrocket.com/accessing-previous-props-state-react-hooks/
>
> https://www.youtube.com/watch?v=3m3UaEvQkhQ
>
> https://legacy.reactjs.org/docs/hooks-state.html
>
> https://www.w3schools.com/react/react_usestate.asp

<h2 align="center"> 
	🎲 Hands on R004 🎲
</h2>

1. Crie um botão de decremento para o contador, mas não permita valores negativos.

2. Crie um botão que zere o contador.

<center>

[🏠 Home](../index.md)

</center>
