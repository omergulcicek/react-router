<h1>Switch</h1>

Konumla eşleşen ilk `<Route>` veya `<Redirect>` childını oluşturur.

<h2>Route grubu kullanmaktan farkı nedir?</h2>

`<Switch>`, yalnızca bir route oluşturması bakımından benzersizdir. Aksine, konumla eşleşen her bir `<Route>`, kapsamlı bir şekilde oluşturulur. Bu kodu düşünün:

```jsx
<Route path="/about" component={About}/>
<Route path="/:user" component={User}/>
<Route component={NoMatch}/>
```

URL `/about` ise, `<About>`, `<User>` ve `<NoMatch>` hepsi  eşleştiğinden render edilecektir. Bu tasarımlarımıza sidebar, breadcrumb, bootstrap tabları vb. gibi birçok şeyi oluşturmamıza izin veriyor.

Bununla birlikte bazen render etmek için  yalnızca bir tane `<Route>` seçmek istiyoruz. Eğer konum `/`de olursa, aynı zamanda `/:user` ile eşleştirmek istemiyoruz (ya da “404” sayfamızı gösterelim). Switch ile yapabilirsiniz:

```jsx
import { Switch, Route } from 'react-router'

<Switch>
  <Route exact path="/" component={Home}/>
  <Route path="/about" component={About}/>
  <Route path="/:user" component={User}/>
  <Route component={NoMatch}/>
</Switch>
```

Bu, eşleştirilen `<Route>`, öncekiyle aynı konumda oluşturulduğundan, animasyonlu geçişler için de yararlıdır.

```jsx
<Fade>
  <Switch>
    {/* Burada sadece bir child olacak */}
    <Route/>
    <Route/>
  </Switch>
</Fade>

<Fade>
  <Route/>
  <Route/>
  {/* Burada her zaman iki child olacak,
  bir tane null bile olsa
  geçişler biraz daha hantaldır */}
</Fade>
```

<h2>Parametreleri</h2>

<h3>location: object</h3>

Geçerli geçmiş konumu yerine (<i>genellikle mevcut tarayıcı URL'i</i>) child elementlerini eşleştirmek için kullanılacak bir konum objesidir.

<h3>children: node</h3>

`<Switch>`in tüm childları `<Route>` veya `<Redirect>` elementleri olmalıdır. Sadece mevcut konumla eşleşen ilk child render edilecektir.

`<Switch>`e bir konum propsu verilirse, eşleşen child elemanındaki konum propsu geçersiz kılacaktır.

```jsx
<Switch>
  <Route exact path="/" component={Home}/>

  <Route path="/users" component={Users}/>
  <Redirect from="/accounts" to="/users"/>

  <Route component={NoMatch}/>
</Switch>
```

<i>Gelişmiş kılavuzlar sonlanmıştır. Bu aşamadan sonra <b>Uygulamalı Eğitime</b> geçiş yapılacaktır.</i>

<a href="https://omergulcicek.github.io/react-router/uygulamali-egitim/basit-router-ornegi">Sıradaki Eğitim: Basit Router Örneği</a>
