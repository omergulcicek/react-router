<h1>Index Route</h1>

`/` adresini ziyaret ettiğimizde uygulamada sadece boş bir sayfa açar. Orada bir index componenti oluşturmak istiyoruz. Bir `Home` componenti oluşturup sonra `/` dizininde nasıl render edeceğimiz hakkında konuşalım.

```js
// modules/Home.js
import React from 'react'

export default React.createClass({
  render() {
    return <div>Home</div>
  }
})
```

Farklı bir yol ise, eğer `App` componentinin children componentleri varsa onları, yoksa  `Home` componentini çağırmak.

```js
// modules/App.js
import Home from './Home'

// ...
<div>
  {/* ... */}
  {this.props.children || <Home/>}
</div>
//...
```

Unutmayın biz küçük parçalar oluşturacağız, büyük tek parça bir component değil. O yüzden componentleri olabildiğince mantıklı parçalara ayırın.

`index.js` dosyasına yeni bir route ekleyelim.

```js
// index.js
// new imports:
// add `IndexRoute` to 'react-router' imports
import { Router, Route, hashHistory, IndexRoute } from 'react-router'
// ve Home componentini ekleyelim
import Home from './modules/Home'

// ...

render((
  <Router history={hashHistory}>
    <Route path="/" component={App}>

      {/* adres `/` olduğunda yüklenecek index componenti */}
      <IndexRoute component={Home}/>

      <Route path="/repos" component={Repos}>
        <Route path="/repos/:userName/:repoName" component={Repo}/>
      </Route>
      <Route path="/about" component={About}/>
    </Route>
  </Router>
), document.getElementById('app'))
```

Routelar kafanızı karıştırmış olabilir ama aslında oldukça basit. `IndexRoute`u, bir web sayfası `/` konumundayken `index.html`i açması gibi düşünün.

<a href="https://omergulcicek.github.io/react-router/index-link">Sıradaki Eğitim: Index Link</a>
