<h1>Scroll Sorununun Çözümü</h1>

React Router ile geliştirme yaparken şöyle bir sorunla karılaşabiliyorsunuz. Her clickte sayfa yenilenmediği için, scroll aşağıda kaldıysa yeni açılan sayfada da scroll aşağıda kalıyor.

Çözüm yolu içinse, site her update olduğunda scrollu en tepeye getirebiliriz.

`ScrollTop.js` adında bir component oluşturalım.

```js
import { Component } from "react";
import { withRouter } from "react-router-dom";

class ScrollToTop extends Component {
  componentDidUpdate(prevProps) {
    if (this.props.location !== prevProps.location) {
      window.scrollTo(0, 0);
    }
  }

  render() {
    return this.props.children;
  }
}

export default withRouter(ScrollToTop);
```

Yazdığımız kodları ise bu ScrollTop componentinin içerisine alalım.

```jsx
import React, { Component } from "react";
import { BrowserRouter, Route, Switch } from "react-router-dom";

import ScrollTop from "./ScrollTop";
...
...
...
export default class App extends Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <BrowserRouter>
        <ScrollTop>
          <Switch>
            <Route path="/" component={Home} />
            ...
            ...
            ...
          </Switch>
        </ScrollTop>
      </BrowserRouter>
    );
  }
}

```
