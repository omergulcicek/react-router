<h1>Yanlış Adres (404)</h1>

`Link` ve `Route` componentlerinin ilişkilerini daha önceki konularda çokça ele aldık. Kısaca tekrarlamak gerekirse `Link` componenti URL'i güncellerken, `Route` componenti URL'e göre ekrana component basacaktır. Peki ya linkteki URL, herhangi bir `Route` componenti ile eşleşmiyorsa? Bu durumda `path` attribute'ü yazılmamış bir `Route` componenti işimizi görecektir.

İlk olarak kullanacağımız `react` ve `react-router-dom` componentlerini sayfaya dahil edelim.

```js
import React from "react";
import {
  BrowserRouter as Router,
  Route,
  Link,
  Switch,
  Redirect
} from "react-router-dom";
```

Ardından componentimizi oluşturalım.

```jsx
const NoMatchExample = () => (
  <Router>
    <div>
      <ul>
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <Link to="/old-match">Old Match, to be redirected</Link>
        </li>
        <li>
          <Link to="/will-match">Will Match</Link>
        </li>
        <li>
          <Link to="/will-not-match">Will Not Match</Link>
        </li>
        <li>
          <Link to="/also/will/not/match">Also Will Not Match</Link>
        </li>
      </ul>
      <Switch>
        <Route path="/" exact component={Home} />
        <Redirect from="/old-match" to="/will-match" />
        <Route path="/will-match" component={WillMatch} />
        <Route component={NoMatch} />
      </Switch>
    </div>
  </Router>
);
```

Yukarıdaki kodu biraz inceleyelim. `Link`, `Switch`, `Route` ve `Redirect` componentleri kullanılmış. Bu componentler ile alakalı anlamadığınız bir nokta varsa ilgili linklere giderek dokümanı tekrardan okuyabilirsiniz.

* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/link">Link</a>

* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/switch">Switch</a>

* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/route">Route</a>

* <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/redirect">Redirect</a>

Dikkat ederseniz 2. `Link` componentinin set ettiği URL `/old-math` fakat `Redirect` componenti ile bu linke gelindiğinde linki `/will-match` olarak güncelliyoruz. `/` ve `/will-math` URL'leri ile eşleşildiğinde ilgili componentler ekrana yazdırılacaktır.

`/will-not-match` ve `/also/will/not/match` URL'leri ile eşleşen bir `Route` olmadağı için `Route={NoMatch}` render edilerek `NoMatch` componenti ekrana yazdırılacaktır.

```jsx
const Home = () => <h3>Ana Sayfa</h3>;

const WillMatch = () => <h3>Eşleşti!</h3>;

const NoMatch = ({ location }) => (
  <div>
    <h3>
      {location.pathname} linki ile eşleşen bir component bulunamadı.
    </h3>
  </div>
);

export default NoMatchExample;
```

<a href="https://reacttraining.com/react-router/web/example/no-match">Kendi dokümanı</a> üzerinden kodu inceleyebilir ve nasıl çalıştığını test edebilirsiniz.

<a href="https://omergulcicek.github.io/react-router/uygulamali-egitim/scroll-sorunun-cozumu">Sıradaki Eğitim: Scroll Sorunun Çözümü</a>
