<h1>Daha Fazla Nesting</h1>

İlk olarak, `Repos` route'u içerisinde `Repo` route'unu yerleştirin. Sonra `Repos`taki `this.props.children`ı render edin.

```js
// index.js
// ...
<Route path="/repos" component={Repos}>
  <Route path="/repos/:userName/:repoName" component={Repo}/>
</Route>
```

```js
// Repos.js
// ...
<div>
  <h2>Repos</h2>
  <ul>
    <li><Link to="/repos/reactjs/react-router">React Router</Link></li>
    <li><Link to="/repos/facebook/react">React</Link></li>
  </ul>
  {/* Linkimiz /repos/:userName/:repoName olduğunda `Repo.js` render edilecek. */}
  {this.props.children}
</div>
```

<h2>Aktif Linkler</h2>

Daha önce oluşturduğumuz `NavLink`imizi kullanalım, böylece `active` sınıf adını bu bağlantılara eklemiş olacağız:

```js
// modules/Repos.js
// import it
import NavLink from './NavLink'

// ...
<li><NavLink to="/repos/reactjs/react-router">React Router</NavLink></li>
<li><NavLink to="/repos/facebook/react">React</NavLink></li>
// ...
```

<a href="https://omergulcicek.github.io/react-router/hizli-baslangic/index-route">Sıradaki Eğitim: Index Route</a>
