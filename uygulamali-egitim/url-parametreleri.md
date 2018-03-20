<h1>URL Parametreleri</h1>

`match` parametresi üzerinden URL parametresine ulaşabiliriz.

Hızlıca bir örnek üzerinden test edelim.

İlk olarak gerekli `react` ve `react-router-dom` componentlerini sayfaya dahil edelim.

```js
import React from "react";
import { BrowserRouter as Router, Route, Link } from "react-router-dom";
```

Ardından componentimizi oluşturalım. `Link` ve `Route` componentlerinin kullanımını daha öncede görmüştük.

```jsx
const ParamsExample = () => (
  <Router>
    <div>
      <h2>Accounts</h2>
      <ul>
        <li>
          <Link to="/netflix">Netflix</Link>
        </li>
        <li>
          <Link to="/zillow-group">Zillow Group</Link>
        </li>
        <li>
          <Link to="/yahoo">Yahoo</Link>
        </li>
        <li>
          <Link to="/modus-create">Modus Create</Link>
        </li>
      </ul>

      <Route path="/:id" component={Child} />
    </div>
  </Router>
);
```

Yukarıdaki kodda `Link` componentleri URL'i güncellerken, `Route` componenti ise linkteki parametreyi `path="/:id"` ile bir nevi `id` değişkeninde tutmuş oluyor.

Ardından `Child` componentimizi oluşturalım. Fonksiyon component olarak tanımladığımız için `match` objesini parametre olarak aldık. Class component ile oluşturuyorsak, props üzerinden match objesine şu şekilde ulaşabilirdik:

```js
const match = this.props.match;
```

`Child` componentinde ise `match.params.id` ile URL parametresini ekrana yazdırıyoruz.

Böylece (<i>yukarıdaki `ParamsExample` componentinde</i>) linklere tıklandıkça URL güncellenecek, ardından bu URL `Child` componentine basılacak.

```jsx
const Child = ({ match }) => (
  <div>
    <h3>ID: {match.params.id}</h3>
  </div>
);

export default ParamsExample;
```

<a href="https://reacttraining.com/react-router/web/example/url-params">Kendi dokümanı</a> üzerinden kodu inceleyebilir ve nasıl çalıştığını test edebilirsiniz.

<a href="https://omergulcicek.github.io/react-router/uygulamali-egitim/yanlis-adres-404">Sıradaki Eğitim: Yanlış Adres (404)</a>
