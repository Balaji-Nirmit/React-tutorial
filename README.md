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
+ can also use the syntax ` condition && statement_to_be_returned_when_condition_is_true `

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

# functional updates
+ use (existingPosts)=>[postData,...existingPost] to avoid stale values during asynchronous updates

# context API
+ prop drilling:- context API addresses prop drilling; component composition is an alternative
+ folder setup:- use a store folder for context files
+ initialization:- use react.createContext with initial state and export it
+ provider: implement with contextName.provider in component
+ access value:- use the useContext Hook
+ Dynamic Data:- combine context value with state
+ export function:- context can also export function for actions
+ logic separation:- this helps keeps the UI and business logic separate from each other

The Context API in React provides a way to share values (state or functions) between components without having to explicitly pass props through every level of the component tree. It's often used to manage global state or share data across components that are not directly connected in the component hierarchy.

```jsx
import { createContext } from "react";

export const ItemContext=createContext();

// createContext() can take initial value of the context
// this is named export so we have to import it in {}
```
this is ItemContext.jsx

```jsx
import Button1 from "./Button1";
import Hello from "./Hello";
import Fragment from "./Fragment";
import Forms from "./Forms";
import { ItemContext } from "./store/ItemContext";
function App(){
  let items=["iron man","captain america"];
  const handleButton=(event)=>{
    console.log(event)
  }
  return (<ItemContext.Provider value={items}>
    <div>
    <h1>hello world</h1>

    <Button1></Button1>
    <Hello></Hello>
    <Fragment items={items} handleButton={(event)=>handleButton(event)}>
      <h1>yo wai mo</h1>
      <p>welcome to the hidden leaf</p>
    </Fragment>
    <Forms></Forms>
  </div></ItemContext.Provider>)
}
export default App;
```
App.jsx

whenever want to use the context api use useContext hook

```jsx
const itemFromContext=useContext(ItemContext);
```
import the useContext and ItemContext

# use Reducer hook
The useReducer hook in React is a more advanced alternative to useState. It is useful for managing complex state logic where the next state depends on the previous state. This hook is often preferred when dealing with state transitions that require more logic than just updating simple values, for example, when handling forms, animations, or managing state with multiple conditions.

useReducer takes two arguments:

+ A reducer function, which specifies how the state should change based on an action.
+ An initial state.


+ Centralized State Management: When dealing with complex state logic (e.g., multiple actions affecting various state values), a single reducer function can manage it all.
+ Clear and Predictable Updates: Reducers make state transitions explicit and easy to follow, which is especially helpful in debugging.
+ Scalability: As your app grows, managing more state transitions with useReducer can be cleaner and easier than using multiple useState hooks.
+ Performance Optimization: useReducer can be more performant than useState for complex state management because it allows you to handle updates in a more optimized way.

```jsx
import {useReducer} from "react";

const ItemReducer=(state,action)=>{
  if(action.type==="NEW_ITEM"){
    return action.payload.textData
  }
  else if(action.type==="DELETE_ITEM"){
    return "deleted"
  }
}

const Fragment=()=>{

  let [gettextState,dispatchTextState]=useReducer(ItemReducer,"initialValueofreducer")
  // useReducer takes reducer method and initial value
  const textChange = (event) => {
    const textData = event.target.value;
    dispatchTextState({
      type: "DELETE_ITEM",
      payload: { textData },
    });
  };
  
  return (<>
    <input type='text'  onChange={(event)=>textChange(event)}></input>
    {gettextState}
  </>);
}
export default Fragment;
```
# data fetching using Fetch
```js
fetch('https://dummyjson.com/posts')
.then(res => res.json())
.then(console.log);
```

fetch functions returns a promise.
+ default is get method; for post use method:'POST'
+ Errors: doesn't reject on HTTP errors. Check response.ok
+ Headers: managed using Headers API
# useEffect hook
+ handles side effects like data fetching and event handling
+ this run automatically after every render by default
+ By providing a dependency array, it will run when specified variables change. An empty array means the effect runs once.
+ multiple useEffect hooks can be used in a single component for oragnising different side effects separately.
```js
useEffect(()=>{
 //method comes here
},[])
```
[] is passed here means it will run only once otherwise an infinite loop would be initiated (runs at initial rendering)

# handling loading state
+ we can use useState for this
+ setFetching(true) before calling the API and setFetching(false) after calling the API
+ and then use the value of fetching of useState to show loading status

# useEffect hook cleanup
+ return a function from useEffect allows for a cleanuo, ideal for removing event listeners
```js
useEffect(()=>{
  const timerId=setInterval(()=>{
    //do something
  },1000);

  // this is the cleanup function
  return()=>{
     clearInterval(timerId);
  };
},[]);
```

# advanced useEffect
```js
useEffect(()=>{
  const controller =new AbortController();
  const signal=controller.signal;
  fetch('/api/users',{signal})
  .then((res)=>res.json())
  .then((data)=>{
     setUser(data);
  });

 return()=>{
     controller.abort();
 };
},[id]);
```

# why the app was rendering twice?
+ this anomoly doesn't arise in poduction mode
+ it is due to strictmode of the main.jsx or index.jsx

# useCallback hook
+ memoization: preserves functions across renders to prevent un-necessary re renders
+ optimization: enhances performance in components with frequent updates
+ dependency array: recreates the function only when specific dependencies changes
```js
useCallback(callback method,[dependencies])
```
# useMemo hook
+ useEffect executes a function when its dependencies gets changed
+ useCallback returns a method and changes the definition of the method when the dependencies gets changed
+ useMemo caches the result of expensive calculations to enhance the performance
+ only recomputes the memoized value when the specific dependencies gets changed
+ helps prevent un-necessary recalculations
```js
useMemo(method,dependency)
```
# custom hooks
```js
const [value,toggle]=useToggle(true)
const [value,{on,off,toggle}]=useBoolean(false)
```
+ allows to extract and reuse component logics
+ combine multiple built-in hooks
+ enable shanring of stateful logic without changing component hierarchy
+ always start with 'use'

# submitting data with Fetch
```js
fetch('api/api/api',{
  headers:{'Content-Type':'application/json; charset=utf-8'},
  method:'POST',
  body:JSON.stringify({
    username:'name',
    email:'email@emial.com',
  })
  })
  .then(res => res.json())
  .then(data => console.log(data));
```
# react router
```bash
npm install react-router-dom
```
+ after version 6+ everything is changed (checkout react router website for reference)
+ RouterProvider:wraps the app for routung capabilities.
+ createBrowserRouter:helps creating the mapping for router
+ declarative routing: easily defines application routes
+ routes are react components
+ layout routes for shared elements
+ route links : link component with to property can be used to avoid reloading
```js
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import {RouterProvider, createBrowserRouter } from 'react-router-dom';
import CreatePost from './components/CreatePost';
import PostList from './components/PostList';

const router=createBrowserRouter([
	{path:"/",
	 element:<App/>,
	 children:[
		{path:"/",element:<PostList/>},
		{path:"/create-post",element:<CreatePost/>},
	]},
])

ReactDOM.createRoot(document.getElementById('root')).render(
	<React.StrictMode>
		<RouterProvider router={router}>
		</RouterProvider>
	</React.StrictMode>
)
```
it is index.jsx file( or main.jsx)
+ outlet component is used to render the children at the correct places
```js
import "./App.css";
import "bootstrap/dist/css/bootstrap.min.css";
import Header from "./components/Header";
import Footer from "./components/Footer";
import Sidebar from "./components/Sidebar";
import {Outlet} from "react-router-dom";
import {useState} from "react";
import PostListProvider from "./store/post-list-store";

export default function App() {
  const [selectedTab,setSelectedTab]=useState("Home");
  
  
  return (
    <>
      <PostListProvider>
      <div className="appContainer">
        <Sidebar selectedTab={selectedTab} setSelectedTab={setSelectedTab}></Sidebar>
        <div className="content">
          <Header></Header>
          <Outlet />
          <Footer></Footer>
        </div>
      </div>
      </PostListProvider>
    </>
  );
}

```
+ useNavigate hook can be used to do navigation programmatically
```js
import {useNavigate} from "react-router-dom";
const navigate = useNavigate();
const method = () => {
  navigate("/path comes here")
}
```
+ be sure to use navigate("path") at specific places like when adding a post use it inside then of addPost method otherwise it would navigate to the page and after navigation it may add the post
+ if using href then whole page would get loaded each time so that's why Link is used
```js
 <Link to="/" className={`nav-link ${selectedTab==="Home" && "active"}`} aria-current="page" >
     <svg className="bi pe-none me-2" width="16" height="16">
          <use xlinkHref="#home"></use>
     </svg>
     Home
</Link>
```
# data fetching using loader
+ loader method can be used to load data before a particular route is executed
+ the loader method must return the data that is loaded or promise
+ data is available in component and all the child components
+ useLoader hook can be used to get the fetched data
+ loading state can also be used
```js
const router=createBrowserRouter([
	{path:"/",
	 element:<App/>,
	 children:[
		{path:"/",element:<PostList/>,loader:() => {}},
		{path:"/create-post",element:<CreatePost/>},
	]},
])
```

# submitting data using action
+ used to perform an action on submission of Forms
+ custom form component need to be used along with name attribute for all inputs
+ action function will get an data object
+ to generate correct request object, method="post" attributre should be used
```
  data.request.formData()
```
this method can be used to get form data object
```
Object.fromEntries(formData)
```
this can be used to get actual input data
+ redirect() response can be returned for navigation after submission

```js
const router=createBrowserRouter([
	{path:"/",
	 element:<App/>,
	 children:[
		{path:"/",element:<PostList/>,loader:() => {}, action:() => {}},
		{path:"/create-post",element:<CreatePost/>},
	]},
])
```

```js
import {Form, redirect} from "react-router-dom";
const CreatePost=()=>{
  return (
    <>
      <Form method="POST">
        <div className="mb-3">
          <label htmlFor="exampleInputEmail1" className="form-label">Email address</label>
          <input type="email" name="email" className="form-control" id="exampleInputEmail1" aria-describedby="emailHelp"/>
          <div id="emailHelp" className="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div className="mb-3">
          <label htmlFor="exampleInputPassword1" className="form-label">Password</label>
          <input type="password" name="password" className="form-control" id="exampleInputPassword1"/>
        </div>
        <div className="mb-3 form-check">
          <input type="checkbox" name="checkbox" className="form-check-input" id="exampleCheck1"/>
          <label className="form-check-label" htmlFor="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" className="btn btn-primary">Submit</button>
      </Form>
    </>
  )
}

export async function createPostData(data){
  const formData = await data.request.formData();
  const postData = Object.fromEntries(formData);
  console.log(postData);
  return redirect("/");
//always need to return action method
  
}     
export default CreatePost;
```

# redux
+ state management for cross component or app-wide state
+ redux is a predictable state management library
+ local state vs cross component state vs App wide state
+ redux is used for app wide state management just like context api
+ it is different from context api is way that we can create multiple context api but only one redux will be created.
+ redux has greater performance
+ context api setup is tough
# how redux works
+ single source: uses a single central store to maintain the entire application state
+ **actions**:  components never directly change the store.Changes to state are made through dispatched actions which describe events
+ **reducers**: actions are processed by reducers, pure functions that return new state
+ **immutable**: state is immutable, every change results in a new state object
+ this is different from useReducer hook

# working with redux
```bash
npm init -y
npm install redux
```
+ import in node
```js
const redux = require('redux')
```
- we need all 4 things
  - reducer
  - store
  - subscriber
  - actions
```bash
node redux-demo.js
```
command to run the node server

# react with redux
```bash
npm install redux
npm install react-redux
```
+ create store folder with index.js file
+ creating the store using
```js
import {createStore} from redux
```
- providing the store with react
  - provider from react redux
```js
<Provider store={store}><App /></Provider>
```
- using the store
  - useSelector hook gets a slice of the store
```js
const counter = useSelector(state=>state.counter);
```
  - Subscription is already setup and only will re-execute when only your slice is changed. Subscription is automatically cleared also
+ Dispatch actions using useDispatch hook

```js
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import { Provider } from 'react-redux'
import counterStore from './store'

ReactDOM.createRoot(document.getElementById('root')).render(
	<React.StrictMode>
		<Provider store={counterStore}><App/></Provider>
	</React.StrictMode>
)
```
index.jsx

```js
import {createStore} from "redux";

const INITIAL_VALUE = {
  counter: 0,
} 

const counterReducer=(store=INITIAL_VALUE,action)=>{
  if(action.type==='INCREMENT'){
    return {counter:store.counter+1}
  }
  else if(action.type==='DECREMENT'){
    return {counter:store.counter-1}
  }
  return store;
}

const counterStore=createStore(counterReducer);
export default counterStore;
```
index.js store

```js
import { useDispatch} from "react-redux";

const Controls=()=>{
  const dispatch = useDispatch();

  const increment = ()=>{
    dispatch({type:"INCREMENT"});
  }
  const decrement = ()=>{
    dispatch({type:"DECREMENT"});
  }
  
  return (
    <>
      <div className="d-grid gap-2 d-sm-flex justify-content-sm-center">
        <button type="button" className="btn btn-primary" onClick={increment}>+1</button>
        <button type="button" className="btn btn-secondary" onClick={decrement}>-1</button>
      </div>
    </>
  )
}
export default Controls;
```
controls.jsx

```js
import { useSelector } from "react-redux";

const DisplayCounter = ()=>{
  const counter = useSelector(state=>state.counter);
  return (
    <>
      <p className="lead mb-4">Counter current value : {counter}</p>
    </>
  )
}
export default DisplayCounter;
```
displaycounter.jsx

if multiple values are there in initial_value

```js
import { useDispatch} from "react-redux";

const Controls=()=>{
  const dispatch = useDispatch();

  const increment = ()=>{
    dispatch({type:"INCREMENT"});
  }
  const decrement = ()=>{
    dispatch({type:"DECREMENT"});
  }

  const checkbox=()=>{
    dispatch({type:"CHECKBOX"});
  }
  
  return (
    <>
      <div className="d-grid gap-2 d-sm-flex justify-content-sm-center">
        <button type="button" className="btn btn-primary" onClick={increment}>+1</button>
        <button type="button" className="btn btn-secondary" onClick={decrement}>-1</button>
        <input type="checkbox" onClick={checkbox}/>
      </div>
    </>
  )
}
export default Controls;
```
control.jsx

```js
import {createStore} from "redux";

const INITIAL_VALUE = {
  counter: 0,
  flag: true,
} 

const counterReducer=(store=INITIAL_VALUE,action)=>{
  if(action.type==='INCREMENT'){
    return {...store,counter:store.counter+1}
  }
  else if(action.type==='DECREMENT'){
    return {...store,counter:store.counter-1}
  }
  else if(action.type==="CHECKBOX"){
    return {...store,flag:!store.flag}
  }
  return store;
}

const counterStore=createStore(counterReducer);
export default counterStore;
```
index.js store
**Note**: always return complete store (shorthand using ... destructuring) otherwise on doing some action the previous value may be lost

# react redux toolkit
## why redux toolkit
+ action  types are difficult to maintain
+ store becoming too big
+ mistakenly editing stores
+ reducer becoming too big
## working with toolkit
```bash
npm install @reduxjs/toolkit
```
+ remove redux from package.json
```js
import {createSlice} from "@redux/toolkit"
```
+ slice of store can be created using following syntax
```js
const slice = createSlice({
  name:"",
  initialState:{},
  reducers:{
    smallReducerMethods:(state,action) => {
    },
  }
})
```
+ configureStore combines multiple reducers and can be used as:
```js
configureStore({
  reducer:{name:slice.reducer}
})
```

```js
export actions=slice.actions;
```
+ actions can be dispatched like:
```js
action.reducerMethod(payload);
```
