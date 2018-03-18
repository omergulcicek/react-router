<h1>Basit Router Örneği</h1>

<a href="https://omergulcicek.github.io/react-router/kurulum/react-router-kurulumu">React Router kurulumu</a>nu tamamladıktan sonra `src/App.js` dosyasına adım adım aşağıdaki kodları ekleyelim.

İlk olarak kullanacağımız componentleri sayfaya dahil edelim.

```js
import React from 'react'
import {
  BrowserRouter as Router,
  Route,
  Link
} from 'react-router-dom'
```

Ardından componentlerimizi oluşturalım. Class componentte kullanabiliriz fakat burada kısa olması açısından fonksiyon component örneği verilmiştir. Aşağıda görüldüğü üzere `Home`, `About` ve `Topics` componentlerini oluşturalım.

```js
const Home = () => (
  <div>
    <h2>Home</h2>
  </div>
)

const About = () => (
  <div>
    <h2>About</h2>
  </div>
)

const Topics = () => (
  <div>
    <h2>Topics</h2>
  </div>
)
```

Ardından bir `Router` componenti kullanarak `Link` ve `Route`larımızı ayarlayalım.

```jsx
const BasicExample = () => (
  <Router>
    <div>
      <ul>
        <li><Link to="/">Home</Link></li>
        <li><Link to="/about">About</Link></li>
        <li><Link to="/topics">Topics</Link></li>
      </ul>

      <hr/>

      <Route exact path="/" component={Home}/>
      <Route path="/about" component={About}/>
      <Route path="/topics" component={Topics}/>
    </div>
  </Router>
)

export default BasicExample
```

`BasicExample` componentinde görüldüğü üzere, `ul` içerisinde `Link` componentleri tanımlanmıştır. Bunlar derlendiğinde `<a>` etiketine dönüşecektir (bknz: <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/link">Link componenti detay</a>).

Bu `Link` componentlerine tıklandığında URL, `to="/"` parametresinde yazan değer ile güncellenecektir. Ardından `Route` componentleri sıralanmıştır.

Burada ise URL, `path="/"` ile eşleştiğinde gerekli component sayfaya dahil edilecektir (bknz: <a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/route">Route componenti detay</a>).

Yani basit olarak react router kullanmak için yapmamız gereken şey, `Link` componentleri ile URL'i set etmek, ardından `Route` componentleri ile URL ile eşleşen componenti yüklemektir.

<a href="https://omergulcicek.github.io/react-router/uygulamali-egitim/url-parametreleri">Sıradaki Eğitim: URL Parametreleri</a>
