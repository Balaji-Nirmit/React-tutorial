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
```
# fragments

Fragments are a way to group multiple elements without introducing an extra DOM node. This helps keep the DOM tree clean and prevents unnecessary wrappers or divs.

```jsx
function Fragment(){
  return <h1>lists</h1>
    <ul>
      <li>iron man</li>
      <li>captain america</li>
    </ul>
  
}
export default Fragment;
```
this will throw error
to solve this we can add all into a div but it will create an additional un-necessary tag so use fragments

```jsx
import React from 'react';
function Fragment(){
  return <React.Fragment><h1>lists</h1>
    <ul>
      <li>iron man</li>
      <li>captain america</li>
    </ul>
  </React.Fragment>
}
export default Fragment;
```

short hand
```jsx
function Fragment(){
  return <>
    <h1>lists</h1>
    <ul>
      <li>iron man</li>
      <li>captain america</li>
    </ul>
  </>
}
export default Fragment;
```
in this method no need to import react

# Map method

```jsx
import React from 'react';
function Fragment(){
  let items=['iron man','captain america']
  return <React.Fragment><h1>lists</h1>
    <ul>
      {items.map(item => <li>{item}</li>)}
    </ul>
  </React.Fragment>
}
export default Fragment;
```
this renders from array data
+ but this will throw error in console to must have a id while rendering a list and this id will also help in reducing time to reload when few items are changed
+ and always use className instead of class
```jsx
{items.map(item => <li className="abc" key={item}>{item}</li>}
```
# conditional rendering

```jsx
import React from 'react';
function Fragment(){
  
  let items=['iron man','captain america'];
  items=[];
  if(items.length===0){
    return <h1>empty</h1>
  }
  return <React.Fragment><h1>lists</h1>
    <ul>
      {items.map(item => <li key={item}>{item}</li>)}
    </ul>
  </React.Fragment>
}
export default Fragment;
```
+ we can also use ternary operator also inside {} into return statement

# passing data via props
+ short for properties
+ mechanism for passing data
+ read only by default
+ passes data from parent to child
+ data flows one way only (downwards)
  
```jsx
const Fragment=(props)=>{
  
  return (<><h1>lists</h1>
    <ul>
      {props.items.map(item => <li key={item}>{item}</li>)}
    </ul>
  </>);
}
export default Fragment;
```
it is Fragment.jsx

```jsx
import Button1 from "./Button1";
import Hello from "./Hello";
import Fragment from "./Fragment";
function App(){
  let items=["iron man","captain america"];
  return <div>
    <h1>hello world</h1>
    <Button1></Button1>
    <Hello></Hello>
    <Fragment items={items}></Fragment>
  </div>
}
export default App;
```
it is App.jsx

```jsx
const Fragment=({items})=>{
  
  return (<><h1>lists</h1>
    <ul>
      {items.map(item => <li key={item}>{item}</li>)}
    </ul>
  </>);
}
export default Fragment;
```
can also do like this using destructuring

# css modules
+ localised class names to avoid global conflicts
+ automatically generates unique class names
+ helps in creating component specific styles
+ styles are scoped to individual components
+ file name must be like this
```bash
component_name.module.css
```
and then import it into the file
```jsx
import styles from './Items.module.css';
```
file name of css here is Items.module.css

```jsx
<li className={`${styles["my-class"]} additional-tailwinf-or-bootsstrap-class`}>hell yeah</li>
```
or 
```jsx
<li className={styles.class}>hell yeah</li>
```
```css
.my-class{
border:2px solid red;
}
```
above the word style is just a name can be css or mystyle or anything

# passing children

+ children is a special prop for passing elements into components
+ used for flexible and reusable design
+ accessed with props.children
+ can be any content: string, numbers ,jsx or components

```jsx
  const Fragment=(props)=>{
  
  return (<><h1>lists</h1>
    <ul>
      {props.items.map(item => <li key={item}>{item}</li>)}
    </ul>
    {props.children}
  </>);}
export default Fragment;
```
this is Fragments.jsx
```jsx
import Button1 from "./Button1";
import Hello from "./Hello";
import Fragment from "./Fragment";
function App(){
  let items=["iron man","captain america"];
  return <div>
    <h1>hello world</h1>
    <Button1></Button1>
    <Hello></Hello>
    <Fragment items={items}>
      <h1>yo wai mo</h1>
      <p>welcome to the hidden leaf</p>
    </Fragment>
  </div>
}
export default App;
```
this is App.jsx

```jsx
const Fragment=({children,items})=>{
  
  return (<><h1>lists</h1>
    <ul>
      {items.map(item => <li key={item}>{item}</li>)}
    </ul>
    {children}
  </>);
}
export default Fragment;
```
can be like this also

# handling events

+ react uses camelCase eg: onClick for events
+ uses synthetic events not browser events
+ event handlers can be functions or arrow functions
+ uses onChange for controlled form inputs
+ avoid inline arrow functions in jsx for performance issues
```jsx
const Fragment=({children,items})=>{
  
  return (<><h1>lists</h1>
    <ul>
      {items.map(item => <li key={item}>{item} <button onClick={()=>console.log('hehe')}>press me</button></li>)}
    </ul>
    {children}
  </>);
}
export default Fragment;
```
can make a separate method above the return statement and call it in onClick
onClick={method_name}

```jsx
 {items.map(item => <li key={item}>{item} <button onClick={(event)=>console.log('hehe')}>press me</button></li>)}
```
can pass event also

# passing functions via props

+ commonly used for event handling
+ parent defines a function and child invokes it
+ enhances component interactively
+ this way upward communication i.e child to parent
```jsx
import Button1 from "./Button1";
import Hello from "./Hello";
import Fragment from "./Fragment";
function App(){
  let items=["iron man","captain america"];
  const handleButton=(event)=>{
    console.log(event)
  }
  return <div>
    <h1>hello world</h1>
    <Button1></Button1>
    <Hello></Hello>
    <Fragment items={items} handleButton={(event)=>handleButton(event)}>
      <h1>yo wai mo</h1>
      <p>welcome to the hidden leaf</p>
    </Fragment>
  </div>
}
export default App;
```
App.jsx
```jsx
const Fragment=({children,items,handleButton})=>{
  
  return (<><h1>lists</h1>
    <ul>
      {items.map(item => <li key={item}>{item} <button onClick={handleButton}>press me</button></li>)}
    </ul>
    {children}
  </>);
}
export default Fragment;
```
Fragment.jsx

# managing state 
+ state represents data that changes over time and is local and private to the component
+ state changes cause components to re-render
+ for functional components use useState hook
+ react functions that start with keyword use are called hooks
+ hooks should only be inside components
+ parent components can pass state down to children via props
+ share state by moving it to their closest common ancestor
useState returns an array with2 elements current value and a method to change the value

```jsx
import { useState } from "react";

const Fragment=({children,items,handleButton})=>{
  let textState=useState("initial value");
  let gettextState=textState[0];
  let settextState=textState[1];
  const textChange=(event)=>{
    settextState(event.target.value);
  }
  
  return (<><h1>lists</h1>
    <ul>
      {items.map(item => <li key={item}>{item} <button onClick={handleButton}>press me</button></li>)}
    </ul>
    {children}
    <input type='text' onChange={(event)=>textChange(event)}></input>
    {gettextState}
  </>);
}
export default Fragment;
```
```jsx
import { useState } from "react";

const Fragment=({children,items,handleButton})=>{
  let [gettextState,settextState]=useState("initial value");
  const textChange=(event)=>{
    settextState(event.target.value);
  }
  
  return (<><h1>lists</h1>
    <ul>
      {items.map(item => <li key={item}>{item} <button onClick={handleButton}>press me</button></li>)}
    </ul>
    {children}
    <input type='text' onChange={(event)=>textChange(event)}></input>
    {gettextState}
  </>);
}
export default Fragment;
```

# react icon library
+ lot of icons without managing them
```bash
npm install react-icons -save
```
```jsx
import {IconName} from "react-icons/fc";
```
```jsx
import { FaHome } from "react-icons/fa";
return <FaHome />
```

# inspecting with react dev tools
+ react dev tool is a chrome extension which can be used to inspect and make changes via browser very easily
+ it shows state and props also
# how react works

- root component
  - the App is the main component or root component of a react application and is the starting point of react component tree
- virtual DOM
  - react creates a in memory structure called virtual DOM which is a lightweight representation where each node stands for component and its attributes
- reconciliation process
  - when component detect changes the react updates the virtual dom state to mirror these changes, then compares the current and previous versions of the virtual DOM, identifies specific nodes they are updating and only those nodes are updated in the real browser DOM

index.html file -> main.jsx

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'

ReactDOM.createRoot(document.getElementById('root')).render(
	<React.StrictMode>
		<App />
	</React.StrictMode>
)
```
this is main.jsx
it has react and react-dom/client imported
+ strictmode helps in notifying the errors while development only not in production
+ ReactDOM converts react dom to actual browser dom
+ if used ReactNative then it would have converted it into android or ios app
+ React's main role is to create dynamic UI and not help in routing,https calls, state management and more

# forms 
+ state management:- each input's state is stored in components' state
+ use onChange to detect changes
+ use onSubmit for form submission and prevent default with event.preventDefault()
+ implement custom validation or use 3rd party libraries

```jsx
import { useState } from "react";

function Forms(){
  let [getName,setName]=useState();
  let [getEmail,setEmail]=useState();
  const submitForm=(event)=>{
    console.log(getName+getEmail);
    event.preventDefault();
  }
  return (<>
    <form onSubmit={submitForm}>
      <input type="text" value={getName} onChange={(event)=>setName(event.target.value)} placeholder="enter your name" />
      <input type="email" value={getEmail} onChange={(event)=>setEmail(event.target.value)} placeholder="enter your email" />
      <button>submit</button>
    </form>
  </>)
}
export default Forms;
```
# use ref
+ allows access to DOM elements and retain mutable values without re-renders
+ used with ref attribute for direct DOM interaction
+ can hold previous state or prop values
+ not limited to DOM references can hold any value
+ Refs can be passed as props also
```jsx
import { useRef} from "react";

function Forms(){
  let getName=useRef();
  let getEmail=useRef();
  const submitForm=(event)=>{
    console.log(getName.current.value+getEmail.current.value);
    event.preventDefault();
  }
  return (<>
    <form onSubmit={submitForm}>
      <input type="text" ref={getName} placeholder="enter your name" />
      <input type="email" ref={getEmail} placeholder="enter your email" />
      <button>submit</button>
    </form>
  </>)
}
export default Forms;
```

# spread operator
```jsx
let arr1=[1,2,3];
let arr2=[...arr1,4,5];
```
here arr2= [1,2,3,4,5]
