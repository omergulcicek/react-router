<h1>Static Router</h1>

Konumu hiçbir zaman değiştirmeyen bir `<Router>`dır. Bu, kullanıcı aslında etrafta tıklama yapmadığı sürece sunucu tarafı oluşturma senaryolarında yararlı olabilir, böylece konum aslında hiç değişmez. Aynı zamanda basit bir testte, yalnızca bir konumu takmanız ve render çıktısı üzerinde onaylamalar yapmanız gerektiğinde faydalıdır. Ayrıca, `<Redirect>` ler için 302 durum kodu ve diğer istekler için normal HTML gönderen bir örnek düğüm sunucusudur.

```js
import { createServer } from 'http'
import React from 'react'
import ReactDOMServer from 'react-dom/server'
import { StaticRouter } from 'react-router'

createServer((req, res) => {

  // Bu obje, render işleminin sonuçlarını içerir
  const context = {}

  const html = ReactDOMServer.renderToString(
    <StaticRouter location={req.url} context={context}>
      <App/>
    </StaticRouter>
  )

  // context.url, bir <Redirect> kullanıldığında yönlendirilecek URL'yi içerecektir
  if (context.url) {
    res.writeHead(302, {
      Location: context.url
    })
    res.end()
  } else {
    res.write(html)
    res.end()
  }
}).listen(3000)
```

<h2>Parametreleri</h2>

<h3>basename: string</h3>

Tüm konumlar için temel URL'dir. Düzgün olarak biçimlendirilmiş bir basename, bir eğik çizgi içermeli, ancak takip eden bir eğik çizgi olmamalıdır.

```js
<StaticRouter basename="/calendar">
  <Link to="/today"/> // <a href="/calendar/today"> şeklinde render edilecektir
</StaticRouter>
```

<h3>location: string</h3>

Sunucudan alınan URL, büyük olasılıkla bir düğüm sunucusunda req.url.

```js
<StaticRouter location={req.url}>
  <App/>
</StaticRouter>
```

<h3>location: object</h3>

`{ pathname, search, hash, state }` gibi bir konum objesi içerir.

```js
<StaticRouter location={req.url}>
  <App/>
</StaticRouter>
```

<h3>context: object</h3>

Düz bir JavaScript objesidir. Render sırasında, componentleri render etmek hakkında bilgi depolamak için objeye özellik ekleyebilir.

```js
<StaticRouter location={-{ pathname: '/bubblegum' }-}>
  <App/>
</StaticRouter>
```

<i>GitHub Pages süslü parantezden (`{`) iki tane yan yana koyulduğunda hata verdiği için araya tire (`-`) koydum, normalde kodda o tireleri yok sayın.</i>

Bir `<Route>` eşleştiğinde, context objesini `staticContext` prop olarak oluşturduğu componente iletir. Render edildikten sonra, bu özellikler sunucunun yanıtını yapılandırmak için kullanılabilir.

```js
if(context.status === '404') {
  // ...
}
```

<h3>children: node</h3>

Bir adet child element render eder.

```js
<StaticRouter>
  <App/>
</StaticRouter>
```

<a href="https://omergulcicek.github.io/react-router/gelismis-kilavuzlar/switch">Sıradaki Gelişmiş Kılavuz: Switch</a>
