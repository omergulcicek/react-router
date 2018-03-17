<h1>Hash Router</h1>

UI'nızı URL ile senkronize tutmak için, hash bölümünü (<i>yani, window.location.hash</i>) kullanan bir `<Router>`dır.

>  Not:
>
>  Hash geçmişi `location.key` veya `location.state`i desteklemez. Önceki sürümlerde bu davranışı değiştirmeye çalıştık, ancak çözemediğimiz sorunlar vardı. Bu davranışa ihtiyaç duyan herhangi bir kod veya eklenti çalışmaz. Bu teknik yalnızca eski tarayıcıları desteklediği için, sunucunuzu `<BrowserHistory>` ile çalışacak şekilde yapılandırmanızı öneririz.


```jsx
import { HashRouter } from 'react-router-dom'

<HashRouter>
  <App />
</HashRouter>
```

<h2>Parametreleri</h2>

<h3>basename: string</h3>

Tüm konumların temel URL'ini belirtir. Uygulamanız sunucunuzdaki bir alt dizinde sunuluyorsa, bunu alt dizine ayarlayabilirsiniz. Başlarında `/` olmalı fakat sonlarında olmamalıdır.

```jsx
<HashRouter basename="/calendar" />
<Link to="/today" /> // <a href="#/calendar/today"> şeklinde render edilecektir.
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

<HashRouter getUserConfirmation={getConfirmation} />
```

<h3>hashType: string</h3>

`window.location.hash` için kullanılacak kodlamanın türüdür. Mevcut değerler şunlardır:

* `slash` - `#/` ve `#/sunshine/lollipops` gibi linkler oluşturur
* `noslash` - `#` ve `#sunshine/lollipops` gibi linkler oluşturur
* `hashbang` - `#!/` ve `#!/sunshine/lollipops` gibi <a href="https://developers.google.com/webmasters/ajax-crawling/docs/learn-more">ajax crawlable</a> (<i>Google tarafından kullanımdan kaldırıldı</i>) linkler oluşturur

Varsayılan değer `slash`dır (`#/`).

<h3>children: node</h3>

Bir adet child element render eder.

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/link">Sıradaki Gelişmiş Kılavuz: Link</a>
