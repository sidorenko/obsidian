#typescript 
```table-of-contents
```
#### TypeScript vs JavaScript
TypeScript добавляет статическую типизацию в JavaScript, делая его более надежным и менее подверженным ошибкам. Он также предлагает функции, которых нет в стандартном JavaScript, такие как классы, интерфейсы и дженерики. Впрочем, весь код на JavaScript валиден и на TypeScript.
#### TS and JS Interoperability
TypeScript полностью совместим с JavaScript. Вы можете включить JavaScript-файлы в свой TypeScript-проект, и TypeScript-код будет компилироваться в JavaScript. TypeScript также предлагает "Declaration Files" (файлы с расширением .d.ts), которые позволяют определять типы для существующего JavaScript-кода. Это означает, что вы можете типизировать свой существующий JavaScript-библиотеки или сторонние библиотеки. 
#### Installation and Configuration
TypeScript можно установить с помощью Node Package Manager (npm):

```shell
npm install -g typescript
```

Далее, вы создаете файл `tsconfig.json` в корне вашего проекта, чтобы настроить TypeScript компилятор.
#### tsconfig.json

`tsconfig.json` - это конфигурационный файл для TypeScript компилятора. Вы можете настроить различные настройки, такие как путь к файлам для компиляции, какой модуль использовать, целевую версию ECMAScript и т.д.

Пример `tsconfig.json` файла:

```json
{
    "compilerOptions": {
        "module": "commonjs",
        "target": "es5",
        "outDir": "dist",
    },
    "include": ["src/**/*"],
    "exclude": ["node_modules"]
}
```
#### Compiler Options
Опции компилятора определяют настройки компиляции для вашего TypeScript проекта. Это включает в себя возможности, связанные с модулями, настройками исходной карты, строгой проверкой типов и многими другими. 

Пример некоторых часто используемых опций:

- `"target": "es5"`: определяет версию ECMAScript для вывода.
- `"module": "commonjs"`: определяет стандарт модуля для использования: 'none', 'commonjs', 'amd', 'system', 'umd', 'es6', 'es2015', 'es2020', или 'ESNext'.
- `"strict": true`: Включает все строгие проверки типов.
- `"noImplicitAny": true`: Выдает ошибку при использовании данных типа 'any', если не указан явно.
- `"outDir": "./dist"`: Каталог для скомпилированных файлов на выходе.
#### tsc
`tsc` это команда TypeScript Compiler, которая компилирует ваш TypeScript-код в JavaScript. 

```shell
tsc myfile.ts
```
#### ts-node
`ts-node` это надстройка над `node`, которая позволяет выполнять TypeScript код без предварительной компиляции. Он полезен для скриптов и автоматизации.

```shell
ts-node myfile.ts
```
#### TS Playground
TS Playground это интерактивная онлайн-платформа, которую создали разработчики TypeScript. Это место, где можно мгновенно запустить TypeScript код прямо в браузере без установки или настройки окружения.

[TypeScript Playground](https://www.typescriptlang.org/play)
