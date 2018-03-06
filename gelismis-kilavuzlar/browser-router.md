<h1>BrowserRouter</h1>

UI'ızı URL ile senkronize tutmak için HTML5 history API'sini (<i>pushState, replaceState ve popstate eventi</i>) kullanan bir `<Router>`dır.

<i>`BrowserRouter` kullanmak için `react-router-dom`dan import edip basitçe aşağıdaki gibi kullanabiliriz.</i>

```js
import { BrowserRouter } from 'react-router-dom'

<BrowserRouter
  basename={}
  forceRefresh={}
  getUserConfirmation={}
  keyLength={}
>
  <App/>
</BrowserRouter>
```

<h2>Parametreleri</h2>

<h3>basename: string</h3>

Tüm konumların temel URL'ini belirtir. Uygulamanız sunucunuzdaki bir alt dizinde sunuluyorsa, bunu alt dizine ayarlayabilirsiniz. Başlarında `/` olmalı fakat sonlarında olmamalıdır.

```js
<BrowserRouter basename="/calendar"/>
<Link to="/today"/> // <a href="/calendar/today"> şeklinde render edilecektir.
```

<i>HTML'deki `<base href="" />` tag'ı ile aynı mantıkta çalışır.</i>

<h3>getUserConfirmation: func</h3>

Gezinmeyi onaylamak için kullanılacak bir fonksiyondur. Varsayılan <a href="https://developer.mozilla.org/en-US/docs/Web/API/Window/confirm">window.confirm</a> komutunu kullanır.

```js
// bu varsayılan davranıştır
const getConfirmation = (message, callback) => {
  const allowTransition = window.confirm(message)
  callback(allowTransition)
}

<BrowserRouter getUserConfirmation={getConfirmation}/>
```

<h3>forceRefresh: bool</h3>

`forceRefresh` parametresi `true` ise, router sayfa gezinirken sayfayı komple yenileyecektir. Büyük olasılıkla bunu yalnızca HTML5 history API'sini desteklemeyen tarayıcılarda kullanırsınız.

```js
const supportsHistory = 'pushState' in window.history
<BrowserRouter forceRefresh={!supportsHistory}/>
```

<h3>keyLength: number</h3>

`location.key` uzunluğudur, varsayılan olarak 6'dır.

```js
<BrowserRouter keyLength={12}/>
```

<h3>children: node</h3>

Bir adet child element render eder.

```js
<BrowserRouter keyLength={12}/>
```

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/hash-router">Sıradaki Gelişmiş Kılavuz: HashRouter</a>
