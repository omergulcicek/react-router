<h1>MemoryRouter</h1>

URL'inizin geçmişini belleğinde tutan (adres çubuğunu okumayan veya yazmayan) bir `<Router>`dır. React Native gibi tarayıcı olmayan ortamlarda kullanışlıdır.

<i>`MemoryRouter` kullanmak için `react-router-dom`dan import edip basitçe aşağıdaki gibi kullanabiliriz.</i>

```js
import { MemoryRouter } from 'react-router-dom'

<MemoryRouter>
  <App/>
</MemoryRouter>
```

<h2>Parametreleri</h2>

<h3>initialEntries: array</h3>

Geçmiş yığındaki bir konumun dizisidir. Bunlar `{pathname, search, hash, state}` yada basit string URL'leri olan tam kapsamlı konum nesneleri olabilir.

```jsx
<MemoryRouter
  initialEntries={[ '/one', '/two', { pathname: '/three' } ]}
  initialIndex={1}
>
  <App/>
</MemoryRouter>
```

<h3>initialIndex: number</h3>

İlk giriş dizilimindeki başlangıç konum dizinidir.

```jsx
<NavLink
  to="/faq"
  activeStyle={{
    fontWeight: 'bold',
    color: 'red'
   }}
>FAQs</NavLink>
```

<h3>keyLength: number</h3>

Konum uzunluğudur. Varsayılan değer 6'dır.

```jsx
<MemoryRouter keyLength={12}/>
```

<h3>children: node</h3>

Bir adet child element render eder.

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/redirect">Sıradaki Gelişmiş Kılavuz: Redirect</a>
