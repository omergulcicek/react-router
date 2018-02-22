<h1>React Router Kurulumu</h1>

React projesine başlamanın en kolay yolu, bir Facebook projesi olan `Create React App` başlangıç kitini kullanmaktır.

Öncelikle `create-react-app` uygulamasını yüklemediyseniz yükleyin ve ardından yeni bir proje oluşturun.

<i>Create React App ile ilgili detaylı bilgi için <a href="https://omergulcicek.github.io/reactjs/reactjs-kurulumu">react js kurulumu</a>nda ilgili başlığı okuyabilirsiniz.</i>

Aşağıdaki komutlar ile `create-react-app`ı indirip, `demo-app` adında bir proje oluşturabiliriz.

```sh
npm install -g create-react-app
create-react-app demo-app
cd demo-app
```

<h2>Kurulum</h2>

React Router DOM, `npm` veya `yarn` yardımı ile kurabilirsiniz.

```sh
npm install react-router-dom

//yada yarn ile kurulum yapmak istiyorsak
yarn add react-router-dom
```

Aşağıdaki kod örneğinde olduğu gibi `src/App.js` dosyasında `react-router-dom`u projenize import edebilirsiniz.

```js
import React from 'react'
import {
  BrowserRouter as Router,
  Route,
  Link
} from 'react-router-dom'
```

<i>Componentlerin detaylarına ilerleyen sayfalarda girilecektir ve uygulamalı olarak açıklanacaktır.</i>

<i>Kurulumu tamamladıktan sonra hızlı başlangı bölümünden okumaya devam edebilirsiniz. Ardından her component ayrıntılı olarak anlatılacak ve örnekler ile uygulamalı eğitime geçilecektir.</i>

<a href="https://omergulcicek.github.io/react-router/route-render-etmek">İlk Konu: Route Render Etmek</a>
