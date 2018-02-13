<h1>Link ile Gezinmek</h1>

Belki de uygulamanızda en çok kullanılan component `Link`tir. Bu component kullandığınız `<a>` etiketiyle hemen hemen aynıdır.

`App` componentimizde bazı linkler oluşturalım.

```js
// modules/App.js dosyası
import React from 'react'
import { Link } from 'react-router'

export default React.createClass({
  render() {
    return (
      <div>
        <h1>React Router Türkçe Dokümantasyon</h1>
        <ul role="nav">
          <li><Link to="/about">Hakkında</Link></li>
          <li><Link to="/repos">Repos</Link></li>
        </ul>
      </div>
    )
  }
})
```

<a href="http://localhost:8080">http://localhost:8080</a> linkini ziyaret edin ve linklere tıklayın, sayfada geri gidin, tekrar ileri gidin.

<i>`Link` componentine click yaptığımız anda `to=""` parametresinde yazan kısmı sayfa linkine ekler. Fakat sadece linki değiştirir, ekranda o linkteki componentlerin yüklenmesi işlemini ileride `Route` componentleri yardımı ile yapacağız.</i>

<a href="https://omergulcicek.github.io/react-router/ic-ice-gecmis-routelar">Sıradaki Eğitim: İç İçe Geçmiş Routelar</a> 
