<h1 align="center">
<br>React Hook
</h1>

React Hooks são uma nova adição ao React 16.8 que permitem que você use o estado e outros recursos do React sem escrever uma classe. Eles são criados usando funções JavaScript e permitem que você compartilhe código entre componentes React.

Hooks são uma maneira de extrair lógica de componentes React para reutilizar em outros componentes. Ao invés de escrever código complexo em um único componente, você pode usar hooks para extrair lógica para reutilizar em outros componentes.

Hooks também permitem que você use o estado e outros recursos do React sem escrever uma classe. Ao invés de usar classes, você pode usar hooks para gerenciar o estado e outros recursos do React.

Hooks também permitem que você escreva código mais limpo e enxuto. Ao invés de escrever código complexo em um único componente, você pode usar hooks para extrair lógica para reutilizar em outros componentes.

## useState

O hook useState permite que você crie um estado para seu componente React. Ele é usado para armazenar dados que podem ser alterados pelo usuário ou por outros eventos.

Exemplo:
```js
import React, { useState } from 'react';
function App() {
  // Declara uma nova variável de state, que chamaremos de "count"
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
```

## useEffect

O hook useEffect é usado para executar efeitos colaterais em seu componente React. Ele é chamado após cada renderização do componente e pode ser usado para executar tarefas como fazer solicitações de API, ouvir eventos do mouse ou teclado, etc.

Exemplo:
```js
// useEffect com dependência
import { useState, useEffect } from 'react';
function App() {
  const [count, setCount] = useState(0);
  // Executará a função toda vez que o count for alterado
  useEffect(() => {
    document.title = `Você clicou ${count} vezes`;
  }, [count]);
  return (
    <div>
      <h1>Você clicou {count} vezes</h1>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```
```js
// useEffect sem dependência
import { useState, useEffect } from 'react';
function App() {
  const [count, setCount] = useState(0);
  // Executará a função apenas uma vez
  useEffect(() => {
    document.title = `Você clicou ${count} vezes`;
  }, []);
  return (
    <div>
      <h1>Você clicou {count} vezes</h1>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

## useContext: 

O hook useContext é usado para acessar o contexto do React. Ele é usado para compartilhar dados entre componentes sem ter que passar os dados manualmente por toda a árvore de componentes.

Exemplo:
```js
import React, { useContext } from 'react';
// Criamos o contexto
const MyContext = React.createContext();
function App() {
  // Usamos o useContext para ler os dados do contexto
  const value = useContext(MyContext);
  return (
    <div>
      <p>{value}</p>
    </div>
  );
}
export default App;
```

## useReducer

O hook useReducer é usado para gerenciar o estado de seu componente React. Ele é usado para criar um estado gerenciado que pode ser alterado por ações.

Exemplo:
```js
import React, { useReducer } from 'react';
// Criamos o reducer
const reducer = (state, action) => {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
};
function App() {
  // Usamos o useReducer para gerenciar o estado
  const [state, dispatch] = useReducer(reducer, { count: 0 });
  return (
    <div>
      <p>Você clicou {state.count} vezes</p>
      <button onClick={() => dispatch({ type: 'increment' })}>
        +
      </button>
      <button onClick={() => dispatch({ type: 'decrement' })}>
        -
      </button>
    </div>
  );
}
export default App;
```

## Custom hooks

Um hook customizado é um hook criado por você para reutilizar lógica em seus componentes React. Você pode criar hooks customizados para qualquer tipo de lógica que você deseja reutilizar em seus componentes.

Exemplo:
```js
// useCounter.js
import { useState } from 'react';
export default function useCounter(initialCount = 0) {
  const [count, setCount] = useState(initialCount);
  const increment = () => {
    setCount(count + 1);
  };
  const decrement = () => {
    setCount(count - 1);
  };
  return [count, increment, decrement];
}
```
```js
// App.js
import React from 'react';
import useCounter from './useCounter';
function App() {
  const [count, increment, decrement] = useCounter(0);
  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>Incrementar</button>
      <button onClick={decrement}>Decrementar</button>
    </div>
  );
}
export default App;
```

<div align="center">
  <br/>
  <br/>
  <br/>
    <div>
      <sub>Copyright © 2023 - <a href="https://github.com/robertolima-dev">robertolima-dev</sub></a>
    </div>
    <br/>
    <p> 
      <a href="https://github.com/robertolima-dev/licenca/blob/main/LICENSE.md">LICENÇA</a>
    </p>
</div>
