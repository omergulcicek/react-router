<h1>Temiz URL</h1>

Dikkat etmişsinizdir, uygulamamızdaki URL'ler `#` (hash) üzerine inşaa edilmiştir. Varsayılandır ve her zaman çalışır ancak daha temiz url'ler için iyi bir yol vardır.

Modern tarayıcılar JavaScript'in bir http isteği yapmadan URL'i manipüle etmesine izin veriyor. Bu nedenle, yönlendirme yapmak için URL'nin `#` bölümüne güvenmemiz gerekmiyor.

<h2>Tarayıcı Geçmişini Yapılandırma</h2>

`index.js` dosyasını açın ve `hashHistory` yerine `browserHistory` alanını import edin.

```js
// index.js
// ...
// `hashHistory` yerine `browserHistory`
import { Router, Route, browserHistory, IndexRoute } from 'react-router'

render((
  <Router history={browserHistory}>
    {/* ... */}
  </Router>
), document.getElementById('app'))
```

Şimdi uygulamanızı kaydedin ve değişikliği inceleyin, artık temiz url'e sahipsiniz.

<h2>Sunucunuzu Yapılandırma<h2>

Sunucunuzun URL'i ne olursa olsun uygulamanızın açılması gerekiyor, çünkü uygulamanız tarayıcıda URL'i yönlendiriyor. Mevcut sunucumuz URL'i nasıl işleyeceğini bilmiyor.

Webpack Dev Server, bunu etkinleştirmek için bir seçeneğe sahiptir. `package.json` dosyasını açın ve `--history-api-fallback` komutunu ekleyin.

```json
    "start": "webpack-dev-server --inline --content-base . --history-api-fallback"
```

Ayrıca `index.html`deki yolları değiştirmemiz gerekiyor çünkü URL'ler derin yollarda olacak ve uygulama derin bir yolla başlıyorsa dosyaları bulamayacaktır.

```html
<!-- index.html -->
<!-- index.css -> /index.css -->
<link rel="stylesheet" href="/index.css">

<!-- bundle.js -> /bundle.js -->
<script src="/bundle.js"></script>
```

Sunucunuz çalışıyorsa durdurun ve sonra tekrar `npm start` komutu ile çalışın. Sorunsuz çalıştırmayı başardıysanız url'lerinizde # işareti olmadan temiz url'leri görmüş olmanız gerekiyor.

<i>Konu anlatımları sonlanmıştır. Bu aşamadan sonra Gelişmiş Kılavuzlar konularına geçiş yapılacaktır.</i>

<a href="https://omergulcicek.github.io/reactjs/browser-router">Sıradaki Gelişmiş Kılavuz: BrowserRouter</a>
