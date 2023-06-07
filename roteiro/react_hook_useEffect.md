<center>

[🏠 Home](../index.md)

</center>

#

<h1 align="center">Hooks State - useEffect</h1>

## O que é useEffect?

> O useEffectGancho permite que você execute efeitos colaterais em seus componentes.Alguns exemplos de efeitos colaterais são: buscar dados, atualizar diretamente o DOM e temporizadores.
>
> Fonte: https://www.w3schools.com/react/react_useeffect.asp

Crie um arquivo arquivo chamado Effect.tsx, e execute o comando **tsrfce**. Com base nos códigos anteriores vamos criar uma nova versão com dois contadores. O primeiro botão ao ser clicado não altera o estado de nenhum componente, e os outros dois ao serem clicados alteram respectivamente o contador 1 e 2. Perceba que toda vez que qualquer um dos states é alterado o código dentro de useEffect é executado.

```typescript
import React, { useEffect, useState } from "react";
function Effect() {
  const [count, setCount] = useState(0);
  const [count2, setCount2] = useState(0);
  useEffect(() => {
    console.log("Roda a cada renderização");
  });
  return (
    <div>
      <p>Contador 1: {count}</p>
      <p>Contador 2: {count2}</p>
      {/* onClick que tem função que não renderiza tela */}
      <button onClick={() => console.log("tete")}>Não renderiza</button>
      {/* onClick vinculado ao hook */}
      <button onClick={() => setCount((prevCount) => prevCount + 1)}>
        + Contador 1
      </button>
      <button onClick={() => setCount2((prevCount) => prevCount + 1)}>
        + Contador 2
      </button>
    </div>
  );
}
export default Effect;
```

Existem algumas situações que é preciso ter comportamento distintos ao ser alterado um state, ou se quer comportamentos diferentes de acordo com o componente. Para ter o **useEffect** personalizado, basta passar como argumento o state que se deseja observar, conforme o código a seguir:

```typescript
useEffect(() => {
  console.log("Alteração no primeiro state");
}, [count]);
```

Existem situações que é preciso que rode apenas no momento em que a página é carregada, para isso basta passar uma array vazia como parâmetro para o **useEffect**.

```typescript
useEffect(() => {
  console.log("Chamada ao carregar a página");
}, []);
```

Podemos aprimorar esse exemplo para fazer nossa primeira requisição para uma API externa, conforme exemplo a seguir, onde fazemos uma requisição a API STAPI, solicitando um personagem com base no parâmetro uid:CHMA0000289509.

```typescript
import React, { useEffect, useState } from "react";
function Effect() {
  const [count, setCount] = useState(0);
  const [count2, setCount2] = useState(0);
  useEffect(() => {
    console.log("Roda a cada renderização");
  });
  useEffect(() => {
    console.log("Alteração no primeiro state");
  }, [count]);
  interface Character {
    name: string;
    dayOfBirth: string;
    monthOfBirth: string;
    yearOfBirth: string;
    placeOfBirth: string;
  }
  const [character, setCharacter] = useState<Character | null>();
  useEffect(() => {
    console.log("- Start Effect on load page ");
    fetch("https://stapi.co/api/v1/rest/character?uid=CHMA0000289509")
      .then((res) => res.json())
      .then((json) => {
        console.log("--");
        console.log(json);
        setCharacter(json.character);
      });
    console.log("- End Effect on load page ");
  }, []);
  return (
    <div>
      <p>Contador 1: {count}</p>
      <p>Contador 2: {count2}</p>
      {/* onClick que tem função que não renderiza tela */}
      <button onClick={() => console.log("teste")}>Não renderiza</button>
      {/* onClick vinculado ao hook */}
      <button onClick={() => setCount((prevCount) => prevCount + 1)}>
        + Contador 1
      </button>
      <button onClick={() => setCount2((prevCount) => prevCount + 1)}>
        + Contador 2
      </button>

      {character && (
        <div>
          <h2>{character.name}</h2>
          <p>
            Data de nascimento: {character.dayOfBirth}/{character.monthOfBirth}/
            {character.yearOfBirth}
          </p>
          <p>Local de nascimento: {character.placeOfBirth}</p>
        </div>
      )}
    </div>
  );
}
export default Effect;
```

Podemos também utilizar o useEffect juntamente com a requisição de uma API para fazermos a nossa primeira página com busca. Crie um arquivo arquivo chamado ListApi.tsx, e execute o comando **tsrfce**. Para fazer isso vamos novamente utilizar a STAPI, vamos fazer uma requisição das 100 primeiras especies da sua base e vamos fazer uma listagem desses itens.

```typescript
import React, { useEffect, useState } from "react";
//Primeiro vamos definir a interface do nosso objeto, nesse primeiro momento vamos listar apenas o nome.
interface Specie {
  name: string;
}

function ListApi() {
  //Criar o useState com a lista de especies
  const [species, setSpecies] = useState<Specie[]>([]);
  //Fazer a requisição para a API assim que carregar a página, solicitando as 100 primeiras especies
  useEffect(() => {
    fetch(
      "https://stapi.co/api/v2/rest/species/search?pageNumber=1&pageSize=100"
    )
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        setSpecies(data.species);
      });
  }, []);
  return (
    //Exibir na tela
    <div>
      <ul>
        {species?.map((specie) => {
          return <li key={specie.name}>{specie.name}</li>;
        })}
      </ul>
    </div>
  );
}

export default ListApi;
```

Agora com a nossa busca funcionando vamos adicionar a opção de pesquisa.

```typescript
import React, { useEffect, useState } from "react";

interface Specie {
  name: string;
  uid: string;
  humanoide: boolean;
}

function ListApi() {
  const [species, setSpecies] = useState<Specie[]>([]);
  //Incuir o useState para o campo de busca.
  const [search, setSearch] = useState("");
  const filteredSpecies =
    search.length > 0
      ? species.filter((repo) => repo.name.includes(search))
      : [];
  //fim
  useEffect(() => {
    fetch(
      "https://stapi.co/api/v2/rest/species/search?pageNumber=1&pageSize=100"
    )
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        setSpecies(data.species);
      });
  }, []);
  return (
    //Inclusão do input e da condicional de busca
    <div>
      <input
        name="search"
        placeholder="Buscar..."
        value={search}
        onChange={(e) => setSearch(e.target.value)}
        type="text"
      />
      <ul>
        {search.length > 0
          ? filteredSpecies?.map((specie) => {
              return <li key={specie.name}>{specie.name}</li>;
            })
          : species?.map((specie) => {
              return <li key={specie.name}>{specie.name}</li>;
            })}
      </ul>
    </div>
  );
}
export default ListApi;
```

> Referências:
>
> https://www.w3schools.com/react/react_useeffect.asp/
>
> https://www.treinaweb.com.br/blog/react-conheca-o-poder-dos-hooks
>
> https://www.youtube.com/watch?v=ojzuilNld1s
>
> https://www.youtube.com/watch?v=kCpca2z2cls

<h2 align="center"> 
	🎲 Hands on R005 🎲
</h2>

1. Explique o que acontece se usarmos o fetch fora do useEffect.
1. Explique como funciona a função fetch.
1. Adicione 2 campos para serem exibidos no ListaApi.
1. Com base na documentação do STAPI ou de outra de sua preferência crie uma nova listagem.

<center>

[🏠 Home](../index.md)

</center>
