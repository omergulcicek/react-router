<h1>Link</h1>

Uygulamanızın içerisinde gezinme olanağı sağlar.

<i>HTML'deki `<a href="">` tagı ile benzer mantıkta çalışır.</i>

<i>`Link` kullanmak için `react-router-dom`dan import edip basitçe aşağıdaki gibi kullanabiliriz.</i>

```jsx
import { Link } from 'react-router-dom'

<Link to="/about">About</Link>
```

<h2>Parametreleri</h2>

<h3>to: string</h3>

Gidilecek olan adres satırıdır.

<i>HTML'deki `<a href="">` tagının `href=""` kısmı gibi düşünebiliriz. `Link` componentine tıklandığında, `to=""` kısmında yazılan adrese gider.</i>

```jsx
<Link to='/courses?sort=name'/>
```

<h3>to: object</h3>

`to` parametresi objede olabilir.

Bir obje aşağıdaki özelliklerden herhangi birine sahip olabilir:

* `pathname`: Bağlanılacak yolu temsil eden bir string.
* `search`: Sorgu parametrelerini temsil eden bir string
* `hash`: URL'i yerleştirmek için bir # ör. # Bir karması.
* `state`: State'in bulunduğu yere devam etmesi.

```jsx
<Link to={{
  pathname: '/courses',
  search: '?sort=name',
  hash: '#the-hash',
  state: { fromDashboard: true }
}}/>
```

<h3>replace: bool</h3>

`replace` parametresi `true` olduğunda bağlantıya tıklarsak, linke yeni bir konum eklemek yerine geçmiş linkteki geçerli konumun yerini alacaktır.

```jsx
<Link to="/courses" replace />
```

<i>Normalde linkleri uç uca ekler, replace ile önceki linkin yerine geçecektir.</i>

<h3>innerRef: function</h3>

Componentin temel `ref` değerine erişime izin verir.

```jsx
const refCallback = node => { }

<Link to="/" innerRef={refCallback} />
```

<h3>diğerleri</h3>

Ayrıca `<a>` tagında olduğu gibi, örneğin bir title, id, className vb. olmak üzere parametrelere props olarak geçebiliriz.

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/nav-link">Sıradaki Gelişmiş Kılavuz: NavLink</a>
