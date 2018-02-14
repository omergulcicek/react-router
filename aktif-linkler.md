<h1>Aktif Linkler</h1>

`Link`in `a`dan farkı, Link etkin olduğunda farklı stil yada class tanımlayabiliriz.

<h2>Aktif Stiller</h2>

Inline css'in nasıl göründüğüne bakalım, `Link`lerinize `activeStyle` ekleyin.

```js
// modules/App.js
<li><Link to="/about" activeStyle={{ color: 'red' }}>About</Link></li>
<li><Link to="/repos" activeStyle={{ color: 'red' }}>Repos</Link></li>
```

Linklerden aktif olanı kırmızı renkte görünecektir.

<h2>Aktif Class</h2>

Inline CSS'ler yerine aktif bir sınıf adı da kullanabilirsiniz.

```js
// modules/App.js
<li><Link to="/about" activeClassName="active">About</Link></li>
<li><Link to="/repos" activeClassName="active">Repos</Link></li>
```

Aktif olan link `active` classını alacaktır. Şimdi ihtiyacımız olan css dosyamız üzerinden bu classa renk vermek.

```html
// index.html
<link rel="stylesheet" href="index.css" />
```

Ve CSS dosyamızda:

```css
// index.css
.active {
  color: green;
}
```

Tarayıcıyı yenileyerek test edebilirsiniz.

<h2>NavLink Kapsayıcısı</h2>

Sitenizdeki çoğu bağlantı aktif olduklarını bilmek zorunda değildir; genellikle yalnızca birincil gezinme linkleri bunu bilmek zorundadır. `activeClassName` veya `activeStyle`ı her seferinde yazmak zorunda kalmamak için bunlar için bir kapsayıcı component kullanmak mantıklıdır.

Burada, üç noktalı bir spread operatör kullanacağız. `activeClassName`i istediğimiz componente yazmayı sağlar.

`Modules/NavLink.js` konumunda şöyle yeni bir dosya oluşturun:

```js
// modules/NavLink.js
import React from 'react'
import { Link } from 'react-router'

export default React.createClass({
  render() {
    return <Link {...this.props} activeClassName="active"/>
  }
})
```

Şimdi ise linklerimizi `NavLink` ile değiştirelim.

```js
// modules/App.js
import NavLink from './NavLink'

// ...

<li><NavLink to="/about">About</NavLink></li>
<li><NavLink to="/repos">Repos</NavLink></li>
```

<i>Burada yapılan işlem, her seferinde linke `activeStyle` yada `activeClassName` yazmak yerine, bunu halihazırda yazan bir component tanımlıyoruz. `NavLink` componenti bize `activeClassName="active"` yazan bir `Link` componenti return ediyor.
```js
//bu kod yerine
<Link to="/about" activeClassName="active"/>

//bu kodu kullandık
<NavLink to="/about">About</NavLink>
```

Daha kısa, daha anlaşılır ve daha temiz.
</i>

<a href="https://omergulcicek.github.io/react-router/parametreler">Sıradaki Eğitim: Parametreler</a>
