<h1>Index Link</h1>

Uygulamamızda, `Home` componentini return etmek için herhangi bir navigasyona sahip olmadığımızı fark ettiniz mi?

`/`ya bir bağlantı ekleyin ve ne olacağını görün:

```js
// in App.js
// ...
<li><NavLink to="/">Home</NavLink></li>
// ...
```

Garip bir şey fark ettiniz mi? `Home` bağlantısı her zaman aktiftir. Daha önce öğrendiğimiz gibi, kapsayıcı route etkin olduğunda child routelar etkin durumda oluyor. Bunun sebebi ne yazık ki `/` her şeyin kapsayıcısı olmasıdır.

Bu bağlantı için yalnızca dizin yolu etkinken etkinleştirilmesini istiyoruz. `index route` yalnızca dizin yolu render edildiğinde aktif sınıfı (veya css kodlarını) ekler.

<h2>Index Link</h2>

İlk önce `NavLink` yerine` IndexLink` kullanalım.

```js
// App.js
import { IndexLink } from 'react-router'

// ...
<li><IndexLink to="/" activeClassName="active">Home</IndexLink></li>
```

Çözüldü! Şimdi link yalnızca index routetayken aktif olacaktır.

<h2>`onlyActiveOnIndex` Property</h2>

`Link` componentine `onlyActiveOnIndex` propsu ekleyerekte kullanabilirsiniz.

```js
<li><Link to="/" activeClassName="active" onlyActiveOnIndex={true}>Home</Link></li>
```

Zaten `activeClassName`in `Nav` ile ne olduğunu öğrenmiştik.

Unutmayın, `NavLink` de, tüm props alanlarımızı `{...spread}` syntaxı ile `Link`e geçiriyoruz, bu nedenle bir `NavLink` oluştururken props ekleyebiliriz:

```js
<li><NavLink to="/" onlyActiveOnIndex={true}>Home</NavLink></li>
```

<a href="https://omergulcicek.github.io/react-router/temiz-url">Sıradaki Eğitim: Temiz URL</a>
