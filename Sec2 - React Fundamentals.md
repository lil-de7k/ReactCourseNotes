***
##### What is React?
 A JavaScript Library for building user interface.
***
##### Why React?
Single Page Application ,  Client Side Library ,  Build complex UI easily , Components
***
##### How React Work
![how-react-work](how-react-work.png)
***
##### First Code
```html
<div id="root"></div>
```
```jsx
ReactDom.render( <h2>hello from react</h2> , document.getElementById('root') );
```
![1st-react-code](1st-react-code.png)
***
##### App Component
```html
<div id="root"></div>
```

```jsx
const App = () => {
   return (
      <div>
         <h1>first test</h1>
         <h3>22first test</h3>
      </div>
   )
}
ReactDom.render( <App/> , document.getElementById('root') );
```
![app-component](app-component.png)
***
##### JavaScript inside HTML
```html
<div id="root"></div>
```
```jsx
const App = () => {
   const name = "ahmed";
   return (
      <div>
         <h1>{name}</h1>
         <h3>22first test</h3>
      </div>
   )
}
ReactDom.render( <App/> , document.getElementById('root') );

```
![js-in-html](js-in-html.png)
***
##### Setup
 -> Install `Node.js`
 -> Open `VS Code`
 -> Auto extensions `Auto Close Tag`, `Auto Complete Tag`, `Auto Import`, `Auto Rename Tag`
 -> Another extensions `Babel ES6/ES7`, `Bracket Pair Colorizer`, `ES7 React/Redux`
 -> Open Folder, Terminal, `npm create vite@latest`
 -> Press `Ctrl` + `C` to stop the server! { if you want }
 -> Write in terminal `npm run dev` to open the server again!
 ***
##### File Structure
 -> `index.html`   : the main html file contains the root div.
 -> `index.css`     : the main css file that controls the style of whole project.
 -> `App.jsx`         : the file that collects all components in it.
 -> `main.jsx`       : the file that controls all sub-files including `index.html`, `index.css`, `app.jsx`
 -> `package.json`  : file that collects all dependencies and scripts you use in your project.
 -> `package-lock.json` : file that collects the version of all things you use in your project.
 -> `README.md` : the file that explains your project on GitHub.
 -> `.gitignore` : the file that ignores folders as `node_modules` while publishing.
 -> `public` : the folder that can you access from anywhere in your project.
 -> `src` : the folder that contains all main files in your project.
 -> `assets` : the folder that contains images, ...
***
##### What is JSX?
JSX stands for 'JavaScript XML', & it's a syntax extension to JavaScript based in ES6, the 'newest' version of JavaScript, JSX allows you to write HTML in React by converting HTML into React components.
***
##### What is Babel?
It's a converter that converts modern JavaScript 'ES6' into older versions to allow all browsers to read it.
***
##### HTML vs JSX
```html
<h1 class="">This is Heading</h1>
<form for=""></form>
<p style="color:red; background-color:blue;">I'm a Paragraph</p>
<h3>Enjoy the course!</h3>
```
```jsx
<h1 className="">This is Heading</h1>
<form htmlFor=""></form>
<p style={{color:'red',backgroundColor:'blue'}}>I'm a Paragraph</p>
const heading = "Enjoy the course!";
<h3>{heading}</h3>
```
***
##### Reusability
```jsx
//App.jsx
import React from 'react'
import Navbar from './components/Navbar'
import Card from './components/Card'
const App = () => {
  return (
    <>
       <Navbar />
       <Card />
       <Card />
       <Card />
       <Card />
    </>
  )
}
export default App

/*-----------------------------------------------*/

//Navbar.jsx
import React from 'react'
const Navbar = () => {
  return (
    <>
       {/* Your Code Here! */}
    </>
  )
}
export default Navbar

/*-----------------------------------------------*/

//Card.jsx
import React from 'react'
const Card = () => {
  return (
    <>
       {/* Your Code Here! */}
    </>
  )
}
export default Card
```
***
##### Props
![props](props.png)
```jsx
//App.jsx
import React from 'react'
import Navbar from './components/Navbar'
import Card from './components/Card'
const App = () => {
  return (
    <>
       <Navbar />
       <Card title={"First Card"} img={'./images/first.png'} />
       <Card title={"Second Card"} img={'./images/second.png'} />
       <Card title={"Third Card"} img={'./images/third.png'} />
       <Card title={"Fourth Card"} img={'./images/fourth.png'} />
    </>
  )
}
export default App

/*-----------------------------------------------*/

//Card.jsx
import React from 'react'
const Card = (props) => {
  return (
    <>
       <h1>Welcome to {props.title}</h1>
       <img src={props.img} />
       <button>Enter</button>
    </>
  )
}
export default Card
```
```jsx
//App.jsx
import React from 'react'
import Navbar from './components/Navbar'
import Card from './components/Card'
import first from '../images/first.png'
import second from '../images/second.png'
import third from '../images/third.png'
import fourth from '../images/fourth.png'
const App = () => {
  const data = [
     {title:"First Card", img:first},
     {title:"Second Card", img:second},
     {title:"Third Card", img:third},
     {title:"Fourth Card", img:fourth}]
  return (
    <>
       <Navbar />
       {
           data.map((item, index)=>{
               const title = item.title;
               const image = item.img;
               return(
                   <Card key={index} title={title} img={image} />
               )
           })
       }
    </>
  )
}
export default App

/*-----------------------------------------------*/

//Card.jsx
import React from 'react'
const Card = (props) => {
  return (
    <>
       <h1>Welcome to {props.title}</h1>
       <img src={props.img} />
       <button>Enter</button>
    </>
  )
}
export default Card
```
***
##### Pass functions as props, children
![pass-props](pass-props.png)
```jsx
//Card.jsx
import React from 'react'
const Card = (props) => {
  return (
    <>
       <h1>Welcome to {props.title}</h1>
       <img src={props.img} />
       <button onClick={() => console.log('You Entered!')}>Enter</button>
    </>
  )
}
export default Card

/*-----------------------------------------------*/

import React from 'react'
const Card = (props) => {
  const handleClick = () => {
    console.log('You Entered!');
  }
  return (
    <>
      <h1>Welcome to {props.title}</h1>
      <img src={props.img} />
      <button onClick={handleClick}>Enter</button> {/* بنادي عليها بس */}
      <button onClick={handleClick()}>Enter</button> {/* بشغلها منغير ما ادوس */}
    </>
  )
}
export default Card
```
```jsx
//App.jsx
import React from 'react'
import Navbar from './components/Navbar'
import Card from './components/Card'
import first from '../images/first.png'
import second from '../images/second.png'
import third from '../images/third.png'
import fourth from '../images/fourth.png'
const App = () => {
  const data = [
     {title:"First Card", img:first},
     {title:"Second Card", img:second},
     {title:"Third Card", img:third},
     {title:"Fourth Card", img:fourth}]
  const printTitle = (message) => {
     console.log("This is from App file" + message);
  }
  return (
    <>
       <Navbar />
       {
           data.map((item, index)=>{
               const title = item.title;
               const image = item.img;
               return(
                   <Card key={index} title={title} img={image} 
                   onClick={printTitle} />
               )
           })
       }
    </>
  )
}
export default App

/*-----------------------------------------------*/

//Card.jsx
import React from 'react'
const Card = (props) => {
  const handleClick = () => {
    props.onClick(props.title);
  }
  return (
    <>
       <h1>Welcome to {props.title}</h1>
       <img src={props.img} />
       <button onClick={handleClick}>Enter</button>
    </>
  )
}
export default Card
```
```jsx
//App.jsx
import React from 'react'
import Navbar from './components/Navbar'
import Card from './components/Card'
import first from '../images/first.png'
import second from '../images/second.png'
import third from '../images/third.png'
import fourth from '../images/fourth.png'
const App = () => {
  const data = [
     {title:"First Card", img:first},
     {title:"Second Card", img:second},
     {title:"Third Card", img:third},
     {title:"Fourth Card", img:fourth}]
  const printTitle = (message) => {
     console.log("This is from App file" + message);
  }
  return (
    <>
       <Navbar />
       {
           data.map((item, index)=>{
               const title = item.title;
               const image = item.img;
               return(
                   <Card key={index} title={title} img={image} 
                   onClick={printTitle}>
                       <h1>hello</h1>
                       <p>paragraph</p>
                   </Card>
               )
           })
       }
    </>
  )
}
export default App

/*-----------------------------------------------*/

//Card.jsx
import React from 'react'
const Card = ({title, img, onClick, children}) => {
  const handleClick = () => {
    onClick(title);
  }
  return (
    <>
       <h1>Welcome to {title}</h1>
       <img src={img} />
       <button onClick={handleClick}>Enter</button>
       {children} {/* The 'h1' & 'p' inside the '<Card></Card>' tag! */}
    </>
  )
}
export default Card
```
***
##### Render Lists conditional
```jsx
//App.jsx
import React from 'react'
import Navbar from './components/Navbar'
import Card from './components/Card'
const App = () => {
  const printTitle = (message) => {
     console.log("This is from App file" + message);
  }
  return (
    <>
       <Navbar />
       {
           data.length ?
               (data.map((item, index)=>{
                   const title = item.title;
                   const image = item.img;
                   return(
                       <Card key={index} title={title} img={image} 
                       onClick={printTitle} />
                   )
               })) : (<h2>No Data Found!</h2>)
       }
    </>
  )
}
export default App
```
***
##### Events, Handlers, User Input
```jsx
// onClick  -> Buttons
// onChange -> Inputs
// onSubmit -> Forms

<button onClick={}> Click Me! </button>
<input onChange={}> Search... </input>
<form onSubmit={}> Submit </form>

/*-----------------------------------------------*/

const onChangeHandler = (e) => { console.log(e.target.value); }
<input onChange={onChangeHandler}> Search... </input>

/*-----------------------------------------------*/

const onSubmitHandler = (e) => {
    e.preventDefault();    //prevent the reload after submitting
    console.log(e.target.value);
}
<form onSubmit={onSubmitHandler}> Submit </form>
```
***
##### React Router (Navigation)
 -> In Terminal `npm install react-router-dom`
 
![router](router.png)
```jsx
//App.jsx
import React from 'react'
import Home from './components/Home'
import Navbar from './components/Navbar'
import Content from './components/Content'
import About from './components/About'
import Footer from './components/Footer'
import Error404 from './components/Error404'
import {BrowserRouter, Route, Routes} from 'react-router-dom'
const App = () => {
  return (
     <>
         <Navbar />
         <BrowserRouter>
             <Routes>
                 <Route path='/' element={<Home />} />       {/* new ver. */}
                 <Route path='/' exact element={<Home />} /> {/* old ver. */}
                 <Route path='/content' element={<Content />} />
                 <Route path='/about' element={<About />} />
                 <Route path='/footer' element={<Footer />} />
                 <Route path='*' element={<Error404 />} />
             </Routes>
         </BrowserRouter>
     </>
  )
}
export default App

/*-----------------------------------------------*/

//Home.jsx
import React from 'react'
const Home = () => {
  return (
    <>
       {/* Your Code Here! */}
    </>
  )
}
export default Home

/*-----------------------------------------------*/

//Navbar.jsx
import React from 'react'
import {Link} from 'react-router-dom'
const Navbar = () => {
  return (
    <>
       {/* Your Code Here! */}
       <Link to='/'> Go Home.. </Link>
    </>
  )
}
export default Navbar

/*-----------------------------------------------*/

//Content.jsx
import React from 'react'
import {Link} from 'react-router-dom'
const Content = () => {
  return (
    <>
       {/* Your Code Here! */}
       <Link to='/'> Go Home.. </Link>
    </>
  )
}
export default Content

/*-----------------------------------------------*/

//About.jsx
import React from 'react'
import {Link} from 'react-router-dom'
const About = () => {
  return (
    <>
       {/* Your Code Here! */}
       <Link to='/'> Go Home.. </Link>
    </>
  )
}
export default About

/*-----------------------------------------------*/

//Footer.jsx
import React from 'react'
import {Link} from 'react-router-dom'
const Footer = () => {
  return (
    <>
       {/* Your Code Here! */}
       <Link to='/'> Go Home.. </Link>
    </>
  )
}
export default Footer

/*-----------------------------------------------*/

//Error404.jsx
import React from 'react'
import {Link} from 'react-router-dom'
const Error404 = () => {
  return (
    <>
       {/* Your Code Here! */}
       <Link to='/'> Go Home.. </Link>
    </>
  )
}
export default Error404
```
***
##### React Hooks
![react-hooks](react-hooks.png)
***
##### useState();
![useState](useState.png)
```jsx
//App.jsx
import React from 'react'
import StateExample from './components/StateExample'
const App = () => {
  return (
     <>
         <StateExample />
     </>
  )
}
export default App

/*-----------------------------------------------*/

//StateExample.jsx
import React, {useState} from 'react'
const StateExample = () => {
    const [count,setCount] = useState(0);
    console.log(count); //0
    const addHandler = () => { setCount(count + 1) }
    const minusHandler = () => { setCount(count - 1) }
    return (
        <>
            <button onClick={addHandler}> + </button>
            <button onClick={minusHandler}> - </button>
            <label> Count is {count} </label>
        </>
    )
}
export default StateExample

/*-----------------------------------------------*/

//StateExample.jsx
import React, {useState} from 'react'
const StateExample = () => {
    const [count,setCount] = useState(0);
    const [text,setText] = useState('');
    const textHandler = (e) => {setText(e.target.value)}
    return (
        <>
            <button onClick={() => setCount(count + 1)}> + </button>
            <button onClick={() => setCount(count - 1)}> - </button>
            <label> Count is {count} </label>
            <input type='text' value={text} onChange={textHandler} />
        </>
    )
}
export default StateExample
```
***
##### useEffect();
![useEffect](useEffect.png)
```jsx
//App.jsx
import React from 'react'
import EffectExample from './components/EffectExample'
const App = () => {
  return (
     <>
         <EffectExample />
     </>
  )
}
export default App

/*-----------------------------------------------*/

//EffectExample.jsx
import React, {useState, useEffect} from 'react'
const EffectExample = () => {
    const [count,setCount] = useState(0);
    useEffect( ()=>{
        console.log('hello from useEffect')
    } );  //everytime making re-render this code will run.
    return (
        <>
            <button onClick={() => setCount(count + 1)}> + </button>
            <button onClick={() => setCount(count - 1)}> - </button>
            <label> Count is {count} </label>
        </>
    )
}
export default EffectExample

/*-----------------------------------------------*/

//EffectExample.jsx
import React, {useEffect} from 'react'
const EffectExample = () => {
    useEffect( ()=>{
        console.log('hello from useEffect')
    } , [] );  //will run at first time this component runs.
    return (
        <>
            
        </>
    )
}
export default EffectExample

/*-----------------------------------------------*/

//EffectExample.jsx
import React, {useState, useEffect} from 'react'
const EffectExample = () => {
    const [count,setCount] = useState(0);
    useEffect( ()=>{
        console.log('hello from useEffect')
    } , [count] );  //everytime changing the 'count' this code will run.
    return (
        <>
            <button onClick={() => setCount(count + 1)}> + </button>
            <button onClick={() => setCount(count - 1)}> - </button>
            <label> Count is {count} </label>
        </>
    )
}
export default EffectExample
```
```jsx
// Every re-render
useEffect( () => {
    console.log('I run everytime this component re-renders');
});

/*-----------------------------------------------*/

// On Mount
useEffect( () => {
    console.log('I only run once {when the component gets mounted}');
} , [] );

/*-----------------------------------------------*/

// Condition based
useEffect( () => {
    console.log('I run everytime my condition is changed');
} , [condition] );

/*-----------------------------------------------*/

// Condition based with "clean up"
useEffect( () => {
    console.log('I run everytime my condition is changed');
    return () => {
        // this runs before the actual code!
        console.log('Use this return as a {clean up tool}');
    }
} , [condition] );
```
***
##### useRef();
![useRef](useRef.png)
```jsx
//App.jsx
import React from 'react'
import RefExample from './components/RefExample'
const App = () => {
  return (
     <>
         <RefExample />
     </>
  )
}
export default App

/*-----------------------------------------------*/

//RefExample.jsx
import React, {useRef} from 'react'
const RefExample = () => {
    const value = useRef(null);
    console.log(value); //{current: null}
    const focus = () => {
        value.current.focus();
        console.log(value.current); //<input type="text">
    }
    return (
        <>
            <input type="text" ref={value} />
            <button onClick={focus}> Focus </button>
        </>
    )
}
export default RefExample
```
***
##### useContext(); - P1
![useContext](useContext.png)
```jsx
//App.jsx
import React, {useContext} from 'react'
import {ColorContext} from './components/ContextProvider'
const App = () => {
//5- use context
    const data = useContext(ColorContext);
    return (
        <>
            {data} {/* white */}
        </>
    )
}
export default App

/*-----------------------------------------------*/

//ContextProvider.jsx
import React, {createContext} from 'react'
//1- create context
const ColorContext = createContext();
//2- create provider
const ContextProvider = ({children}) => {
    return (
        <ColorContext.Provider value='white'>
            {children}
        </ColorContext.Provider>
    )
}
//3- export context to use & provider to wrap all components
export { ContextProvider, ColorContext }

/*-----------------------------------------------*/

//main.jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'
import { ContextProvider } from './components/ContextProvider'
//4- import & wrap the 'App' component with 'ContextProvider'
createRoot(document.getElementById('root')).render(
    <StrictMode>
        <ContextProvider>
            <App />
        </ContextProvider>
    </StrictMode>,
)
```
***
##### useContext(); - P2
![useContext](useContext.png)
```jsx
//App.jsx
import React, {useContext} from 'react'
import {ColorContext} from './components/ContextProvider'
import RefExample from './components/RefExample'
const App = () => {
//5- use context
    const {data, changeData} = useContext(ColorContext);
    //changeData('green');
    return (
        <>
            {data} {/* green */}
            <RefExample />
        </>
    )
}
export default App

/*-----------------------------------------------*/

//ContextProvider.jsx
import React, {createContext, useState} from 'react'
//1- create context
const ColorContext = createContext();
//6- update data in context
//2- create provider
const ContextProvider = ({children}) => {
    const [data,setData] = useState('white');
    const changeData = (color) => {
        setData(color);
    }
    return (
        <ColorContext.Provider value={{data, changeData}}>
            {children}
        </ColorContext.Provider>
    )
}
//3- export context to use & provider to wrap all components
export { ContextProvider, ColorContext }

/*-----------------------------------------------*/

//main.jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'
import { ContextProvider } from './components/ContextProvider'
//4- import & wrap the 'App' component with 'ContextProvider'
createRoot(document.getElementById('root')).render(
    <StrictMode>
        <ContextProvider>
            <App />
        </ContextProvider>
    </StrictMode>,
)

/*-----------------------------------------------*/

//RefExample.jsx
import React, {useRef, useContext} from 'react'
import {ColorContext} from './components/ContextProvider'
const RefExample = () => {
    const {data, changeData} = useContext(ColorContext);
    const valueInput = useRef(null);
    console.log(value); //{current: null}
    const focus = () => {
        value.current.focus();
        console.log(valueInput.current); //<input type="text">
        changeData(valueInput.current.value)
    }
    return (
        <>
            <input type="text" ref={valueInput} />
            <button onClick={focus}> Focus </button>
        </>
    )
}
export default RefExample
```
***
##### useMemo();
![useMemo](useMemo.png)
```jsx
//App.jsx
import React from 'react'
import MemoExample from './components/MemoExample'
const App = () => {
  return (
     <>
         <MemoExample />
     </>
  )
}
export default App

/*-----------------------------------------------*/

//MemoExample.jsx
import React, {useState, useMemo} from 'react'
const MemoExample = () => {
    const randomColor = "#"+Math.floor(Math.random()*16777215).toString(16);
    const [counter,setCounter] = useState(0);
    const [test,setTest] = useState(0);
    const result = useMemo(() => {
        return (
            <div style={{ color: randomColor }}>
                2 by {counter} equals: {counter*2}
            </div>
        )
    } , [counter] );
    return (
        <div>
            <button onClick={() => setCounter(counter - 1)}> - </button>
            <button onClick={() => setCounter(counter + 1)}> + </button>
            <button onClick={() => setTest(test + 1)}> test </button>
        </div>
    )
    //color only changes by clicking buttons contains 'counter' state!
}
export default MemoExample
```
***
##### useReducer();
![useReducer](useReducer.png)
```jsx
//App.jsx
import React, {useReducer} from 'react'
import ReducerExample from './components/ReducerExample'
const App = () => {
  return (
     <>
         <ReducerExample />
     </>
  )
}
export default App

/*-----------------------------------------------*/

//ReducerExample.jsx
import React, {useState} from 'react'
const ReducerExample = () => {
    const [value,setValue] = useState(0);
    return (
        <div>
            value is {value}
	        <button onClick={() => setValue(value + 1)}> + </button>
	        <button onClick={() => setValue(value - 1)}> - </button>
	        <button onClick={() => setValue(0)}> reset </button>
        </div>
    )
}
export default ReducerExample

/*-----------------------------------------------*/

//ReducerExample.jsx
import React, {useReducer} from 'react'
const initialValue = { count: 0 }
const reducer = (state, action) => {
    switch(action.type)
    {
        case 'increment':
            return { count: state.count + 1 };
        case 'decrement':
            return { count: state.count - 1 };
        case 'reset':
            return { count: 0 };
        default:
            return state;
    }
}
const ReducerExample = () => {
    const [state, dispatch] = useReducer(reducer, initialValue);
    return (
        <div>
            value is {state.count} {/* {initialValue} '0' */}
	        <button onClick={() => dispatch({type:'increment'})}> + </button>
	        <button onClick={() => dispatch({type:'decrement'})}> - </button>
	        <button onClick={() => dispatch({type:'reset'})}> reset </button>
        </div>
    )
}
export default ReducerExample
```
***
##### Fetching Data API
![fetch-data-api](fetch-data-api.png)
```jsx
//App.jsx
import React, {useReducer} from 'react'
import FetchAxios from './components/FetchAxios'
const App = () => {
  return (
     <>
         <FetchAxios />
     </>
  )
}
export default App

/*-----------------------------------------------*/

//FetchAxios.jsx
import React, {useState, useEffect} from 'react'
const FetchAxios = () => {
    const [state,setState] = useState([]);
    const fetchData = async () => {
        await fetch('https://jsonplaceholder.typicode.com/posts',{
            method:'GET' // GET: receive data , POST: send data
        }).then(response => response.json()).then(data => setState(data))
    };
    useEffect(() => {
        fetchData();
    } , [] )
    return (
        <div>
            {state[0].title} {/* to only check the success! */}
        </div>
    )
}
export default FetchAxios
```

-> To use Axios write in terminal `npm install axios`
```jsx
//App.jsx
import React, {useReducer} from 'react'
import FetchAxios from './components/FetchAxios'
const App = () => {
  return (
     <>
         <FetchAxios />
     </>
  )
}
export default App

/*-----------------------------------------------*/

//FetchAxios.jsx
import React, {useState, useEffect} from 'react'
import axios from 'axios'
const FetchAxios = () => {
    const [state,setState] = useState([]);
    const fetchData = async () => {
        const res = await axios.get('https://jsonplaceholder.typicode.com/posts')
        setState(res.data);
    };
    useEffect(() => {
        fetchData();
    } , [] )
    return (
        <div>
            {state.map((item) => { return (<h3> item.title </h3>) })}
        </div>
    )
}
export default FetchAxios
```