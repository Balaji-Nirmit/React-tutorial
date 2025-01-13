# React-tutorial

+ react is javascript library to create single page application.
+ react create a web page with small and resuable component.
+ React is declarative while js is imperative.

# components
+ app component is the root component.

# create react app
+ official tool is CRA(create react app)
+ vite is mpdern tool to create react app
+ vite produces quick and small bundle size
```bash
npm run dev
```
to launch dev server is created from vite
```bash
npm start
```
use this for CRA
```bash
npm create vite@latest
```
+ this will ask for project name and then ask for library or framework of which choose React and language of typescript and javascript
+ change the directory to the project directory
+ after coming to this directory
```bash
npm install
```
+ this add node module folder to the project
+ use the lauch dev server command to start the project  

# project structure

* node_modules
* public/ directory
- src/ directory: main folder for the react code
  - components/
  - assets/: images and fonts
  - styles/
* package.json: contains info about the project like name, version, dependencies on other react packages
* index.html
* vite.config.js:contains vite config

# file extensions
+ .js
+ .jsx:-stands for javascript XML and this combines javascript with html like tags

# components

## class components
 this is not used now a days
## functional components
 initially stateless and can use hooks for state and effects

# jsx
+ javascript xml
+ determines how the component will look and is not html rather jsx
+ gets converted to javascript behind the scene
+ initially index.html file is executed which call index.jsx or main.jsx which renders the App.jsx file
## creating a component
```js
function file_name(){
}
extport default file_name;
```
here file_name must start with capital letter

```js
import Button1 from "./Button1"
function App(){
return <div>
  <h1>hello world</h1>
  <Button1></Button1>
</div>
}
export default App;
```
to use the component we need to import it

```js
export default function file_name(){
}
```

```js
export function function_name(){
}
export function function_name_2(){
}
```

```js
export function function_name(){
}

export default function_name_2(){
}
```
all the above are ways to make components
+ there can be default export, named exports or default and named exports
+ in react css can be directly imported.
# dynamic component
{} using this 

```js
function Hello(){
  var myName="nirmit pratap singh";
  return <h3>hello bhai i am {myName}</h3>
}
export default Hello;
```

# resuable component
+ modularity: components are modular allowing for easy resuse across different parts of an application
+ efficiency
+ consistency
+ maintenability: changes made to a reused component would be reflected on each and every page that component is used

# including bootstrap
```bash
npm i bootstrap@5.3.2
```
```jsx
import "bootstrap/dist/css/bootstrap.min.css";
