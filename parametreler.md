<h1>Parametreler</h1>

Aşağıdaki URL'leri inceleyelim:

```
/repos/reactjs/react-router
/repos/facebook/react
```

Bu URL'ler şu şekilde bir route yoluyla eşleşir:

```
/repos/:userName/:repoName
```

`:` Ile başlayan parçalar, URL parametreleridir.

<h2>Parametrelerle Route Ekleme</h2>

Uygulamalarımıza, `/repos/:userName/:repoName` dizininde nasıl ekran oluşturacağını öğretelim.

İlk önce route üzerinde render yapmak için bir componente ihtiyacımız var, `modules/Repo.js` dosyasında yeni bir dosya oluşturalım:

```js
// modules/Repo.js
import React from 'react'

export default React.createClass({
  render() {
    return (
      <div>
        <h2>{this.props.params.repoName}</h2>
      </div>
    )
  }
})
```

Şimdi `index.js` dosyasını açın ve yeni route'u ekleyin.

```js
// ...
// import Repo
import Repo from './modules/Repo'

render((
  <Router history={hashHistory}>
    <Route path="/" component={App}>
      <Route path="/repos" component={Repos}/>
      {/* add the new route */}
      <Route path="/repos/:userName/:repoName" component={Repo}/>
      <Route path="/about" component={About}/>
    </Route>
  </Router>
), document.getElementById('app'))
```

Artık, bu yeni route için `Repos.js`de bazı bağlantılar ekleyebiliriz.

```js
// Repos.js
import { Link } from 'react-router'
// ...
export default React.createClass({
  render() {
    return (
      <div>
        <h2>Repos</h2>

        {/* birkaç link ekleyin */}
        <ul>
          <li><Link to="/repos/reactjs/react-router">React Router</Link></li>
          <li><Link to="/repos/facebook/react">React</Link></li>
        </ul>

      </div>
    )
  }
})
```

Şimdi bağlarınızı test edin. Routetaki `path` parametresinin değeri componentte özellik adı olur. Hem `repoName` hem de
`userName`, componentinizin `this.props.params` içerisinde bulunabilir. Kendinize ve başkalarına yardımcı olabilmek adına muhtemelen sonradan bazı props tipleri eklemeniz gerekecek.

<a href="https://omergulcicek.github.io/react-router/daha-fazla-nesting">Sıradaki Eğitim: Daha Fazla Nesting</a>
