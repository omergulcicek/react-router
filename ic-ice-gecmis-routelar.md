<h1>İç İçe Geçmiş Routelar</h1>

`App` componentine eklediğimiz navigasyon muhtemelen her ekranda görünecek. Herhangi bir route olmadan `ul` tag'ı içerisinde bir navigasyon (<i>menü</i>) tanımlayalım ve App componentine ekleyelim.

<h2>İç İçe Geçmiş UI ve URL'ler</h2>

Uygulamamızın bir repo listesi olduğunu farketmişsinizdir; benzer yapı, sadece repo içerikleri farklı olacak. Ayrıca URL'de bununla bağlantılı olacak. Örneğin, url'e `/repos/123` yazdığımızda, bizim componentimiz muhtemelen şu şekilde görünecektir:

```js
<App>       {/*  /          */}
  <Repos>   {/*  /repos     */}
    <Repo/> {/*  /repos/123 */}
  </Repos>
</App>
```

Ve bizim UI'ımız bunun gibi görünecektir.

```
         +-------------------------------------+
         | Home Repos About                    | <- App
         +------+------------------------------+
         |      |                              |
Repos -> | repo |  Repo 1                      |
         |      |                              |
         | repo | Kutuların içindeki kutuların |
         |      | içindeki kutular             | <- Repo
         | repo |                              |
         |      |                              |
         | repo |                              |
         |      |                              |
         +------+------------------------------+
```

<h2>Navigasyonumuzu Paylaşmak</h2>

`About` ve `Repos` componentleri `App` componenti içine yerleştirelim, ardından navigasyonu (<i>home, repos, about yazan menü</i>) uygulamanın tüm ekranlarında görünür olacak şekilde yazalım. Bunu iki adımda yapıyoruz:

Önce, `App` componentini içeren `Route`ın child componente sahip olmasına izin verin ve child componentlerin `path`lerinde yeni rotalar belirleyelim:

```js
// index.js
// ...
render((
  <Router history={hashHistory}>
    <Route path="/" component={App}>
      {/* bunları `App` componentinin childları yapalım */}
      <Route path="/repos" component={Repos}/>
      <Route path="/about" component={About}/>
    </Route>
  </Router>
), document.getElementById('app'))
```

<i>Burada `App` Route'unun bir kapsayıcı olduğunu görüyoruz. Child componenleri olarak `Repos` ve `About` componentlerine sahip. Birazdan `App` componentinin içerisinde `this.props.children` diyerek `Repos` ve `About` Route'larını çağıracağız.</i>

Ardından, child componenleri `App` componentinin içerisinde şu şekle getirin:

```js
// modules/App.js
// ...
  render() {
    return (
      <div>
        <h1>React Router Türkçe Dokümantasyon</h1>
        <ul role="nav">
          <li><Link to="/about">About</Link></li>
          <li><Link to="/repos">Repos</Link></li>
        </ul>

        {/* Bunu ekleyin, altta açıklama yapılmıştır */}
        {this.props.children}

      </div>
    )
  }
// ...
```

<i>`App` componentinin içerisine `this.props.children` yazarak child componentlerin nerede konumlanacağını belirledik.

`<Link to="/about">About</Link>` linkine tıklanırsa `this.props.children` yazan yerde `<About />` componenti görünecek.

`<Link to="/repos">Repos</Link>` linkine tıklanırsa `this.props.children` yazan yerde `<Repos />` componenti görünecek. </i>

React Router, UI'ınızı şu şekilde yapılandırıyor:

```js
// link /about ise
<App>
  <About/>
</App>

// link /repos ise
<App>
  <Repos/>
</App>
```

<h2>Küçük ve Basit Şeylerin Ardından Gelen Harika Şeyler</h2>

Büyük şeyler inşa etmenin en iyi yolu, küçük şeyleri bir araya toplamaktır.

React Router'ın gerçek gücü budur, her route geliştirilebilir. Uygulamalar uygulamaların içinde, kutular kutuların içinde.

`About` route'unu `App` dışına taşırsanız ne olur? Test edebilirsiniz.

<a href="https://omergulcicek.github.io/react-router/aktif-linkler">Sıradaki Eğitim: Aktif Linkler</a>
