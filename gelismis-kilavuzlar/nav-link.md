<h1>NavLink</h1>

Geçerli URL ile eşleştiğinde, render edilmiş elemente css ekleyecek bir `<Link>` sürümüdür.

<i>`Navlink` kullanmak için `react-router-dom`dan import edip basitçe aşağıdaki gibi kullanabiliriz.</i>

```js
import { NavLink } from 'react-router-dom'

<NavLink to="/about">About</NavLink>
```

<i>`NavLink` ile `Link` aynı işi görür fakat NavLink o an sayfada aktif olan linke css kodu/class ekler.</i>

<h2>Parametreleri</h2>

<h3>activeClassName: string</h3>

Element aktif olduğunda ona eklenecek olan sınıfı belirler. Varsayılan olarak `active` sınıfı eklenir. Farklı bir class ismi kullanmak istiyorsak aşağıdaki gibi belirtebiliriz.

```jsx
<NavLink
  to="/faq"
  activeClassName="selected"
>FAQs</NavLink>
```

<h3>activeStyle: object</h3>

Link aktif olduğunda elemana uygulanacak stilleri obje olarak parametre alır.

```jsx
<NavLink
  to="/faq"
  activeStyle={{
    fontWeight: 'bold',
    color: 'red'
   }}
>FAQs</NavLink>
```

<h3>exact: bool</h3>

`true` olduğunda, etkin sınıf/stil yalnızca link ile eşleştiğinde uygulanır.

<i>`exact` yazmazsak `NavLink` kullanıldığında örneğin `/profile` linkindeyken `to="/"` içeren linkte aktif görünecektir. Çünkü `/profile` linki `/` ifadesi içeriyor. `exact` yazdığımızda içeriyor mu diye bakmak yerine eşit mi diye kontrol eder.</i>

```jsx
<NavLink
  exact
  to="/profile"
>Profile</NavLink>
```

<h3>strict: bool</h3>

`true` olduğunda, konumun geçerli URL ile eşleşip eşleşmediğini belirlerken son eğik çizgiside dikkate alınacaktır.

```jsx
<NavLink
  strict
  to="/events/"
>Events</NavLink>
```

<h3>isActive: func</h3>

Bağlantı etkin olduğunda fonksiyon çağırır.

```jsx
const oddEvent = (match, location) => {
  if (!match) {
    return false
  }
  const eventID = parseInt(match.params.eventID)
  return !isNaN(eventID) && eventID % 2 === 1
}

<NavLink
  to="/events/123"
  isActive={oddEvent}
>Event 123</NavLink>
```

<a href="https://omergulcicek.github.io/reactjs/gelismis-kilavuzlar/memory-router">Sıradaki Gelişmiş Kılavuz: MemoryRouter</a>
