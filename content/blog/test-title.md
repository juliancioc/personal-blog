---
path: o-que-é-react-hooks
date: 2020-07-25T02:56:33.169Z
title: O que é React Hooks?
description: Entenda o que é React Hooks, quais são suas funcionalidades e como usar.
---
Para entender melhor o que é React Hooks é necessário saber que para trabalhar com state no React era necessário criar um componente do tipo classe e com isso havia a opção de criar métodos de ciclo de vida como por exemplo:

``` js
componentDidMount() {
    // este método é chamado quando a página é carregada.
}
```

``` js
componentDidUpdate() {
    // este método é chamado quando a página é atualizada.
}
```

Lembre-se que esses métodos não são mais recomendados e na página da documentação oficial do React tem esta informação.

Agora que entendemos que para trabalhar com estado em React era necessário criar um componente do tipo classe e chamar métodos para cada ciclo de vida, vamos conhecer o React Hooks.

O React Hooks está disponível a partir da versão 16.8 do React que foi lançada no dia 06/02/2019 e com o uso dos Hooks não precisamos mais criar um componente do tipo classe e nem chamar os métodos de ciclo de vida para trabalhar com estados e outros recursos do React. Então os Hooks são uma nova forma de trabalhar com estados em página.

<h2>Como trabalhar com state usando React Hooks?</h2>

Para isso temos o useState, é um Hook e o seu uso não é muito diferente do setState que talvez já esteja acosutmado a usar.

``` js
import React, {
    useState
} from 'react';

function Example() {
    // crie uma variável na qual deseja controlar o seu estado
    const [value, setValue] = useState(0);

    return (
        <div>
            <p>O valor atual é {value}</p>
            <button onClick={() => setValue(value + 1)}>
            Clique aqui
            </button>
        </div>
    );
}
```

O que acabamos de fazer foi criar um componente function, definir uma variável para o state com o nome value e sempre que clicar no botão será adicionado 1 à variável.

<h2>Quais são os tipos de Hooks?</h2>

Há muitos tipos de Hooks, irei mostrar os principais mas você pode criar os seus próprios Hooks.

<b>useState</b>: usado para trabalhar com estado do componente.<br /><br />

<b>useEffect</b>: com esse hook você pode executar uma tarefa sempre que uma informação for alterada. Imagine que você precisa criar uma página com paginação e sempre que a página mudar é necessário carregar os novos dados da API, então para esse cenário podemos usar o useEffect. Veja como pode ficar:

``` js
    import React, {
    useState,
    useEffect
} from 'react';

import api from 'sua API'

function Example() {
    // página que será alterada
    const [page, setPage] = useState(1);
    const [items, setItems] = useState([])
    const perPage = 10;

    useEffect(() => {
        api.fetch({
            page: page,
            perPage: perPage
        }).then((response: any) => {
            setItems(response.data);
        })
    }, [page]); // quando esta variável mudar esta função será executada.

    return (
        <div>
            {items.map((item) => {
                console.log(item);
            })}

            <button onClick={() => setValue(page + 1)}>
                Próxima página
            </button>
        </div>
    );
}
```

Com o uso do useState criamos duas variáveis items e page. Quando a página carrega o useEffect irá fazer um fetch na API e no return será mostrado um console com os items que foram retornados.

Temos um botão para a próxima página que irá a altera a variável page e com esta alteração o useEffect será executado novamento retornando mais 10 items da API.

<b>useContext</b>: com este hook você pode distribuir uma informação por toda sua aplicação.<br /><br />

