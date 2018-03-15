<h1>Redirect</h1>

Bir `<Redirect>` işlevi yeni bir konuma yönlendirir. Yeni konum, HTTP 3xx gibi geçerli konumu geçersiz kılacaktır.

<i>`Redirect` kullanmak için `react-router-dom`dan import edip basitçe aşağıdaki gibi kullanabiliriz.</i>

```js
import { Route, Redirect } from 'react-router'

<Route exact path="/" render={() => (
  loggedIn ? (
    <Redirect to="/dashboard"/>
  ) : (
    <PublicHomePage/>
  )
)}/>
```

<h2>Parametreleri</h2>

<h3>to: string</h3>

Yönlendirilecek URL'i temsil eder.

```jsx
<Redirect to="/somewhere/else"/>
```

<h3>to: object</h3>

Yönlendirilecek yeri temsil eder. `pathname`, regexp'in anladığı herhangi bir geçerli URL yolu olabilir.

```jsx
<Redirect to={-{
  pathname: '/login',
  search: '?utm=your+face',
  state: { referrer: currentLocation }
}-}/>
```

<i>GitHub Pages süslü parantezden (`{`) iki tane yan yana koyulduğunda hata verdiği için araya tire (`-`) koydum, normalde kodda o tireleri yok sayın.</i>

`state` objesi, yönlendirilmiş componentte `this.props.location.state` yoluyla erişilebilir. Bu yeni yönlendirme anahtarı (özel bir ad değil) daha sonra, `/login` yol adının işaret ettiği `Login` componentindeki `this.props.location.state.referrer` üzerinden erişilebilir.

<h3>push: bool</h3>

`true` olduğunda yeniden yönlendirme, geçerli olan linkin yerine geçmek yerine geçmişi yeni bir giriş yapar.

```jsx
<Redirect push to="/somewhere/else" />
```

<h3>from: string</h3>

Yönlendirilecek bir yol adını temsil eder. Regexp yolunun anladığı herhangi bir geçerli URL yoludur. Eşleşen tüm URL parametreleri desene ayarlanır. Kullanılmayan ek parametreler göz ardı edilir.

Bu, yalnızca bir <Switch> içinde bir <Redirect> oluştururken bir konumu eşleştirmek için kullanılabilir.

```jsx
<Switch>
  <Redirect from='/old-path' to='/new-path'/>
  <Route path='/new-path' component={Place}/>
</Switch>

// Eşleşen parametrelerle yeniden yönlendirme
<Switch>
  <Redirect from='/users/:id' to='/users/profile/:id'/>
  <Route path='/users/profile/:id' component={Profile}/>
</Switch>
```

<h3>exact: bool</h3>

Tam olarak eşleşmeyi temsil eder. `Route.exact` ile eşdeğerdir.

| path | location.pathname | exact | eşleşiyor mu? |
| ------- | ----------------- | ------------------- | ------------------- |
| /one | /one/two | true | hayır |
| /one | /one/two | false | evet |

<h3>strict: bool</h3>

Kesinlikle eşleşmeyi temsil eder; `Route.strict` ile eşdeğerdir.

`true` olduğunda, eğik çizgi içeren bir yol yalnızca bir `location.pathname` ile başlayan ve eğik çizgi ile eşleşir. Bu, `URL.pathname` öğesine ek URL segmentleri olduğunda hiçbir etkisi yoktur.

| path | location.pathname | eşleşiyor mu? |
| ------- | ----------------- | ------------------- |
| /one/ | /one | hayır |
| /one/ | /one/ | evet |
| /one/ | /one/two | evet |

> Uyarı: `strict`, bir `location.pathname`nin sonunda eğik çizgi bulunmadığından emin olmak için kullanılabilir, ancak bunu yapmak için tam doğru olmalıdır.

| path | location.pathname | eşleşiyor mu? |
| ------- | ----------------- | ------------------- |
| /one/ | /one | evet |
| /one/ | /one/ | hayır |
| /one/ | /one/two | hayır |

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/route">Sıradaki Gelişmiş Kılavuz: Route</a>
