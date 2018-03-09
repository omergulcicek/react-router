<h1>Router</h1>

Tüm router componentleri için ortak alt düzey arayüzüdür. Tipik olarak, uygulamalar altta sıralanmış olan üst düzey routerlardan birini kullanır:

* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/browser-router">Browser Router</a>
* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/hash-router">Hash Router</a>
* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/memory-router">Memory Router</a>
* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/static-router">Static Router</a>

Düşük seviye `<Router>` kullanmak için en yaygın kullanılan durum, bir özel geçmişi, Redux veya Mobx gibi bir state yönetimi kütüphanesiyle senkronize etmektir. React Router'ın yanında state yönetim kütüphanelerini kullanmak için bunun gerekli olmadığını, yalnızca derin entegrasyon için olduğunu unutmayın.

<i>`Router` kullanmak için `react-router-dom`dan import edip basitçe aşağıdaki gibi kullanabiliriz.</i>

```js
import { Router } from 'react-router'
import createBrowserHistory from 'history/createBrowserHistory'

const history = createBrowserHistory()

<Router history={history}>
  <App/>
</Router>
```

<h2>Parametreleri</h2>

<h3>history: object</h3>

Linklerde gezinmek için kullanılacak bir history objesidir.

```js
import createBrowserHistory from 'history/createBrowserHistory'

const customHistory = createBrowserHistory()
<Router history={customHistory}/>
```

<h3>children: node</h3>

Bir adet child element render eder.

```js
<Router>
  <App/>
</Router>
```

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/static-router">Sıradaki Gelişmiş Kılavuz: Static Router</a>
