https://playcode.io/react - online compiler

![[React Map.canvas]]
> [!quote]- Interview Questions by levels:
#### Novice (Junior)
- [[React Component]] Definition (Class-based, Functional)
- [[React Component]] Props (PropTypes typechecking, default prop values)
- [[React Component]] State (initial state, setState, statefull vs stateless components)
- [[React Component]] Lifecycle (mounting, updating, unmounting, phases (render, pre-commit, commit), error boundaries)
- [[React Components]] Сomposition (props.children, composition vs inheritance, lifting state up, practical decomposition task)
- [[React JSX]] (embedding expressions, attributes, childrens)
- [[React DOM]] (createRef, ref forwarding, callback refs, findDOMNode, difference in attributes)
- [[React DOM]] Events (SyntheticEvent, persist event)
- [[React Forms]] (controlled/uncontrolled components)
- [[React Virtual DOM]] (concept, keys)
#### Intermediate (Middle)
- [[React Code Reuse Patterns]]: HOCs
- [[React Code Reuse Patterns]]: Render Props
- [[React Hooks]] (useEffect, useState, useMemo, useCallback, custom hook).
- [[React Code Reuse Patterns]]: React Redux (three main principles, actions, reducers, store, data normalization).
- [[React Code Reuse Patterns]]: React Redux (presentational vs container components, Provider, connect).
- [[React Redux Async Flow]] (middleware, Redux Thunk).
- [[React MobX]] (main principles, observable and computed values, actions, reactions).
- [[React Context]] (when to use, Context.Provider, contextType, Context.Consumer, Context vs Redux).
- [[React Routing]] (react-router, JSX/object configuration, history)
- [[React Animation]] (react-transition-group, manual animation, transition, translate).
- [[React Performance]] (shouldComponentUpdate, keys, stateless components, PureComponent, React.memo).
- [[React React Various Styling]] approaches (styled-components, jss, etc.).
#### Advanced (Senior)
- [[React Virtual DOM]] (reconciliation algorithm, recursing on chilrdren, keys)
- [[React Automated testing]] (Jest/Jasmine/Mocha, Enzyme (shallow, full DOM, static rendering))
- [[React Security]] (XSS on React Props, dangerouslySetInnerHTML)
- [[React Building]] (dev vs production build, babel, webpack, Next.js)
- [[React Server Rendering]] (ReactDOMServer, renderToString, renderToStaticMarkup, renderToNodeStream)
#### Expert

- Know all from Advanced, Intermediate, Novice levels
- Several years of production practice.


#list

```dataview
list from #reactjs SORT file.name ASC
```

> [!question] QUESTION IN ANKI FLASHCARD

#flashcards-react

#### Чи працювали з класовими компонентами? У чому їхня особливість?

#### Які дані краще зберігати в стані компонента, а які передавати через пропси? Наведіть приклад.

#### Чи ознайомлені з хуками? У чому їхні переваги? Чи доводилося робити свої і з якою метою?

#### Чи ознайомлені з фрагментами та порталами? Навіщо вони потрібні?

#### Коли й для чого використовують рефи?

#### Які ви знаєте методи життєвого циклу компонента?

#### В якому методі життєвого циклу компонента краще робити запити на сервер? Чому?

#### В якому методі життєвого циклу компонента краще робити підписку і відписку від лістенера? Чому? Навіщо відписуватися?

#### Чи був досвід роботи з контекстом? Коли його варто використовувати?

#### У чому особливість PureComponent?

#### Чи працював з мемоізованими селекторами (memoized selectors)? Для чого їх використовують і який принцип роботи?

#### У чому бачите переваги бібліотеки React?

#### Чому бібліотека React швидка? Що таке Virtual DOM і Shadow DOM?

#### Навіщо в списках ключі? Чи можна робити ключами індекси елементів масиву? Коли це виправдано?

#### В чому основна ідея Redux?

#### Робота зі стилями в React.

#### React — це бібліотека чи фреймворк? Яка різниця між цими двома поняттями.

#### Чи можна використовувати jQuery разом з React? Чому так / ні?

#### Що таке codemod?

#### Чи доводилося налаштовувати проєкт React з нуля? За допомогою яких інструментів ви це робили?

#### Перерахуйте всі бібліотеки, які використовували у зв’язці з React.

#### Що найскладніше доводилося реалізовувати за допомогою React?

#### Що таке JSX? Що лежить в його основі?

#### Як працює алгоритм Virtual DOM?

#### Для чого потрібна властивість key під час рендерингу списків?

#### У чому різниця між функціональними та класовими компонентами?

#### Навіщо і коли потрібно передавати props в super () при використанні класових компонентів?

#### Чому потрібно використовувати setState () для оновлення внутрішнього стану компонента?

#### У чому полягає принцип «підйому стану»?

#### Які бібліотеки менеджменту стану React-застосунку ви знаєте? Навіщо вони?

#### Коли варто використовувати Redux? Які є альтернативи?

#### Redux vs Mobx?

#### Розкажіть про базовий принцип роботи React Hooks.

#### У чому різниця між createRef і useRef?

#### Коли варто використовувати React refs? Коли не варто?

#### Які недоліки бібліотеки React бачите?

#### Які патерни використовуєте разом з React?

#### Як ставитесь до типізації разом з React?

#### Як побудувати хорошу архітектуру React-проєкту?

#### Оптимізація React-застосунків? Як виміряти продуктивність програми?

#### Чи можна застосунок на React вбудувати в інший застосунок на React?