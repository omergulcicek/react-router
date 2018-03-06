<h1>Route Render Etmek</h1>

`<Router>` bir React Router componentidir.

```js
render(<Router/>, document.getElementById('app'))
```

Bu kod, bir Route yapılandırana kadar hiçbir şey göstermeyecektir.

`index.js` dosyasını açın ve

1. `Router`, `Route` ve  `hashHistory`i import et
2. `App` componentini render et

```js
// ...
import { Router, Route, hashHistory } from 'react-router'

render((
  <Router history={hashHistory}>
    <Route path="/" component={App}/>
  </Router>
), document.getElementById('app'))
```

`npm start` komutu ile çalıştığından emin olun ve daha sonra <a href="http://localhost:8080">http://localhost:8080</a> linkini ziyaret edin.

Aynı ekranı daha önce olduğu gibi (<i>yani router kullanmadan önce sadece App componentini render ettiğimiz halini</i>) almanız gerekir ancak URL'de fazladan gereksiz bir hash (<i>#</i>) karakteri var. Bunun sebebi `HashHistory` kullanıyor olmamız (<i>url'in # kısmı ile yönlendirme geçmişi yönetiliyor</i>). Bunu daha sonra değiştireceğiz ancak şu an için işe yarıyor.

<h2>Daha Fazla Ekran Ekleme</h2>

İki yeni component oluşturun:

- `modules/About.js`
- `modules/Repos.js`

```js
// modules/About.js dosyası
import React from 'react'

export default React.createClass({
  render() {
    return <div>Hakkında</div>
  }
})
```

```js
// modules/Repos.js dosyası
import React from 'react'

export default React.createClass({
  render() {
    return <div>Repos</div>
  }
})
```

Şimdi bunları kendi yollarındaki uygulama ile birleştirelim.

```js
// insert into index.js dosyası
import About from './modules/About'
import Repos from './modules/Repos'

render((
  <Router history={hashHistory}>
    <Route path="/" component={App}/>
    {/* routeları buraya ekle */}
    <Route path="/repos" component={Repos}/>
    <Route path="/about" component={About}/>
  </Router>
), document.getElementById('app'))
```

<a href="http://localhost:8080/#/about">http://localhost:8080/#/about</a> ve <a href="http://localhost:8080/#/repos">http://localhost:8080/#/repos</a> linklerini kontrol edin.

<a href="https://omergulcicek.github.io/react-router/hizli-baslangic/link-ile-gezinmek">Sıradaki Eğitim: Link ile Gezinmek</a>
