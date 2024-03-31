#reactjs 
React Router — это мощная библиотека маршрутизации, которая обеспечивает следование принципам, по которым строится веб (или URL-адреса в вебе) для вашего приложения React. Фактически, React Router — это обертка вокруг компонентов вашего приложения, которая отображает определенные компоненты в зависимости от текущего URL браузера. 

Вам порой нужно создавать Single Page Applications (SPA), где не происходит полная перезагрузка страницы каждый раз при изменении URL. React Router обеспечивает эту функциональность на стороне клиента.

Вот пример базового использования React Router:

```jsx
import React from "react";
import { BrowserRouter as Router, Switch, Route, Link } from "react-router-dom";

export default function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/users">Users</Link>
            </li>
          </ul>
        </nav>


        <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/users">
            <Users />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function Users() {
  return <h2>Users</h2>;
}

```
Тут используются `BrowserRouter`, `Route`, и `Link` компоненты. 

`BrowserRouter` создает историю браузера, которая используется для навигации. `Route` затем просматривает текущую историю URL и отображает некоторый код, когда его путь соответствует текущему URL. Вы можете поместить любой код внутри `Route`, но обычно туда помещают другие компоненты. `Link` компонент представляет собой навигационную ссылку, которая изменяет работник истории URL.

React Router очень мощный и имеет множество дополнительных возможностей, включая защищенные маршруты, динамические маршруты, вложенные маршруты и многое другое.