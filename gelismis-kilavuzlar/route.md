<h1>Route</h1>

Route componenti, React Routerın belki de iyi kullanmayı öğrenmek adına en önemli componenttir. En temel sorumluluğu, bir konumun link ile eşleştiğinde bazı componentleri arayüzde oluşturmaktır.

Aşağıdaki kodu göz önünde bulundurun:

```jsx
import { BrowserRouter as Router, Route } from 'react-router-dom'

<Router>
  <div>
    <Route exact path="/" component={Home} />
    <Route path="/news" component={NewsFeed} />
  </div>
</Router>
```

Uygulamanın konumu `/` ise, UI hiyerarşisi şöyle bir şey olacaktır:

```jsx
<div>
  <Home />
  <!-- react-empty: 2 -->
</div>
```

Uygulamanın konumu `/news` ise, UI hiyerarşisi şöyle bir şey olacaktır:

```jsx
<div>
  <NewsFeed />
  <!-- react-empty: 1 -->
</div>
```

`<!-- react-empt -->` açıklamaları React'in null render etme işleminin yalnızca uygulama ayrıntılarıdır. Bir Route, görüntüsü boş olsa bile her zaman teknik olarak render edilmiştir. Uygulama konumu route yoluyla eşleştiğinde, componenti oluşturulur.

<h3>Route Render Metodları</h3>

Bir `<Route>` render etmek için 3 yol vardır:

* `<Route component>`
* `<Route render>`
* `<Route children>`

Her biri farklı koşullarda faydalıdır. Verilen bir `<Route>` üzerinde bu metodlardan yalnızca birisini kullanmalısınız. Neden 3 seçeneğiniz olduğunu anlamanız için aşağıda açıklamalarına bakın. Çoğu zaman component kullanacaksınız.

<h3>Route Props</h3>

Üç render yönteminin hepsi aynı üç Routeta geçecek

* match
* location
* history

<h2>Parametreleri</h2>

<h3>component</h3>

Yalnızca link eşleştiğinde render edilecek bir React componenti yazılır.

```jsx
<Route path="/user/:username" component={User}/>

const User = ({ match }) => {
  return <h1>Merhaba {match.params.username}!</h1>
}
```

Router, componenti kullandığınızda, verilen componentten yeni bir React elementi oluşturmak için `React.createElement`i kullanır. Component propsunda bir satır içi fonksiyon olarak yazdıysanız, her render edilişinde yeni bir component oluşturursunuz demektir. Bu, mevcut componentin bağlantısını keser ve yalnızca varolan componenti güncelleştirmek yerine yeni component oluşturur. Satır içi render kullanırken, render veya child propsu kullanın (aşağıda).

<h3>render: func</h3>

Bu, yukarıda açıklanan istenmeyen yeniden bağlama olmadan uygun satır içi render etmeye verir.

Component propsunu kullanarak sizin için yeni bir React elementi yaratmak yerine konum eşleştiğinde çağrılabilecek bir fonksiyon yazabilirsiniz.

```jsx
// uygun satır içi render
<Route path="/home" render={() => <div>Home</div>} />

// wrapping/composing
const FadingRoute = ({ component: Component, ...rest }) => (
  <Route {...rest} render={props => (
    <FadeIn>
      <Component {...props} />
    </FadeIn>
  )}/>
)

<FadingRoute path="/cool" component={Something} />
```

>  Uyarı:
>
> `<Route component>`, `<Route render>`dan önceliklidir, bu yüzden her ikisini de aynı yolla kullanmayın.

<h3>children: func</h3>

Bazen yolun konumu ile eşleşip eşleşmediğini belirtmeniz gerekir. Bu gibi durumlarda, children prop fonksiyonunu kullanabilirsiniz. Bir eşleşme olsun veya olmasın denenmesi haricinde çağrılır. Burada, route eşleşiyorsa bir aktif sınıfı ekliyoruz.

```jsx
<ul>
  <ListItemLink to="/somewhere"/>
  <ListItemLink to="/somewhere-else"/>
</ul>

const ListItemLink = ({ to, ...rest }) => (
  <Route path={to} children={({ match }) => (
    <li className={match ? 'active' : ''}>
      <Link to={to} {...rest}/>
    </li>
  )}/>
)
```

<h3>path: string</h3>

<a href="https://www.npmjs.com/package/path-to-regexp">path-to-regexp</a>in anladığı herhangi bir geçerli URL yoludur.

Yol olmayan routelar her zaman eşleşir.

```jsx
<Route path="/users/:id" component={User}/>
```

<h3>exact: bool</h3>

Tam olarak eşleşmeyi temsil eder. `Route.exact` ile eşdeğerdir.

| path | location.pathname | exact | eşleşiyor mu? |
| ------- | ----------------- | ------------------- | ------------------- |
| /one | /one/two | true | hayır |
| /one | /one/two | false | evet |

```jsx
<Route exact path="/one" component={About} />
```

<h3>strict: bool</h3>

Kesinlikle eşleşmeyi temsil eder; `Route.strict` ile eşdeğerdir.

`true` olduğunda, eğik çizgi içeren bir yol yalnızca bir `location.pathname` ile başlayan ve eğik çizgi ile eşleşir. Bu, `URL.pathname` öğesine ek URL segmentleri olduğunda hiçbir etkisi yoktur.

| path | location.pathname | eşleşiyor mu? |
| ------- | ----------------- | ------------------- |
| /one/ | /one | hayır |
| /one/ | /one/ | evet |
| /one/ | /one/two | evet |

```jsx
<Route strict path="/one/" component={About} />
```

> Uyarı: `strict`, bir `location.pathname`nin sonunda eğik çizgi bulunmadığından emin olmak için kullanılabilir, ancak bunu yapmak için tam doğru olmalıdır.

| path | location.pathname | eşleşiyor mu? |
| ------- | ----------------- | ------------------- |
| /one/ | /one | evet |
| /one/ | /one/ | hayır |
| /one/ | /one/two | hayır |

```jsx
<Route exact strict path="/one" component={About} />
```

<h3>sensitive: bool</h3>

`true` olduğunda,  route büyük/küçük harf duyarlı ise eşleşir.

| path | location.pathname | sensitive | eşleşiyor mu? |
| ------- | ----------------- | ------------------- | ------------------- |
| /one | /one | true | evet |
| /One | /one | true | hayır |
| /One | /one | false | evet |

```jsx
<Route sensitive path="/one" component={About} />
```

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/router">Sıradaki Gelişmiş Kılavuz: Router</a>
