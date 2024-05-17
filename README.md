# Desafio Dio - Criando Uma Wiki de Repositórios do GitHub Com React



Projeto completo com passo software tudo mais para criar uma wiki de repositórios do GitHub Com React:

1. #### Crie um novo projeto React usando o seguinte comando:

```plaintext
npx create-react-app wiki
```



1. #### Instale as seguintes dependências:

```plaintext
npm install react-router-dom
npm install axios
npm install react-bootstrap
```



1. #### Crie um novo arquivo chamado `App.js` e adicione o seguinte código:

```plaintext
import React, { useState, useEffect } from "react";
import ReactDOM from "react-dom";
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
import Axios from "axios";
import ReactBootstrap from "react-bootstrap";

const App = () => {
  const [repos, setRepos] = useState([]);

  useEffect(() => {
    Axios.get("https://api.github.com/users/your-username/repos")
      .then((response) => {
        setRepos(response.data);
      })
      .catch((error) => {
        console.log(error);
      });
  }, []);

  return (
    <Router>
      <Switch>
        <Route path="/" exact={true}>
          <ReposList repos={repos} />
        </Route>
        <Route path="/repos/:id" exact={true}>
          <RepoDetails repo={repos.find(repo => repo.id === Number(id))} />
        </Route>
      </Switch>
    </Router>
  );
};

export default App;
```



1. #### Crie um novo arquivo chamado `ReposList.js` e adicione o seguinte código:

```plaintext
import React, { useState, useEffect } from "react";
import ReactBootstrap from "react-bootstrap";

const ReposList = ({ repos }) => {
  const [page, setPage] = useState(1);

  useEffect(() => {
    Axios.get(`https://api.github.com/users/your-username/repos?page=${page}`)
      .then((response) => {
        setRepos(response.data);
      })
      .catch((error) => {
        console.log(error);
      });
  }, [page]);

  return (
    <ReactBootstrap.List>
      {repos.map((repo) => (
        <ReactBootstrap.ListGroupItem key={repo.id}>
          <ReactBootstrap.Link to={`/repos/${repo.id}`}>{repo.name}</ReactBootstrap.Link>
        </ReactBootstrap.ListGroupItem>
      ))}
    </ReactBootstrap.List>
  );
};

export default ReposList;
```



1. #### Crie um novo arquivo chamado `RepoDetails.js` e adicione o seguinte código:

```plaintext
import React, { useState, useEffect } from "react";
import ReactBootstrap from "react-bootstrap";

const RepoDetails = ({ repo }) => {
  return (
    <ReactBootstrap.Card>
      <ReactBootstrap.CardHeader>{repo.name}</ReactBootstrap.CardHeader>
      <ReactBootstrap.CardBody>
        <ReactBootstrap.CardText>
          <p>{repo.description}</p>
          <p>
            <ReactBootstrap.Button href={repo.html_url}>Ver no GitHub</ReactBootstrap.Button>
          </p>
        </ReactBootstrap.CardText>
      </ReactBootstrap.CardBody>
    </ReactBootstrap.Card>
  );
};

export default RepoDetails;
```



1. #### Inicie o servidor de desenvolvimento usando o seguinte comando:

```plaintext
npm start
```



1. #### Abra o navegador e acesse `http://localhost:3000/` para visualizar o projeto.

Este projeto é apenas um exemplo básico de como criar uma wiki de repositórios do GitHub com React. Você pode adicionar mais funcionalidades, como a capacidade de criar e editar páginas, conforme necessário.





# Github Wiki - React

![wiki-1](https://github.com/cintra1/Wiki-Repositorios-React/assets/101955322/0368ffbf-80d6-42e7-9064-8a8a8ad12291)

![wiki-2](https://github.com/cintra1/Wiki-Repositorios-React/assets/101955322/e775e564-2669-41e4-8455-4e0557886699)



## Como acessar

Esse projeto está hospedado no Vercel, clique nesse link para ir para o site: [https://git-find-react.vercel.app/](https://wiki-repositorios-react.vercel.app/)



## Como executar

No diretório do projeto, você pode executar:

### `npm start`

Executa o aplicativo no modo de desenvolvimento.\
Abra [http://localhost:3000](http://localhost:3000) para visualizá-lo em seu navegador.

A página será recarregada quando você fizer alterações.\
Você também pode ver erros de lint no console.



### `npm test`

Inicia o executor de testes no modo de observação interativo.\
Consulte a seção sobre [execução de testes](https://facebook.github.io/create-react-app/docs/running-tests) para obter mais informações.



### `npm run build`

Cria o aplicativo para produção na pasta `build`.\
Ele agrupa corretamente o React no modo de produção e otimiza a construção para obter o melhor desempenho.

A compilação é reduzida e os nomes dos arquivos incluem os hashes.\
Seu aplicativo está pronto para ser implantado!

Consulte a seção sobre [implantação](https://facebook.github.io/create-react-app/docs/deployment) para obter mais informações.



### npm run eject

**Observação: esta é uma operação unidirecional. Depois de `ejetar`, você não pode voltar!**

Se você não estiver satisfeito com a ferramenta de construção e as opções de configuração, você pode `ejetar` a qualquer momento. Este comando removerá a dependência de compilação única do seu projeto.

Em vez disso, ele copiará todos os arquivos de configuração e as dependências transitivas (webpack, Babel, ESLint, etc) diretamente no seu projeto para que você tenha controle total sobre eles. Todos os comandos, exceto `eject`, ainda funcionarão, mas apontarão para os scripts copiados para que você possa ajustá-los. Neste ponto você está sozinho.

Você nunca precisa usar `eject`. O conjunto de recursos selecionados é adequado para implantações pequenas e médias e você não deve se sentir obrigado a usar esse recurso. No entanto, entendemos que esta ferramenta não seria útil se você não pudesse personalizá-la quando estiver pronto para isso.
