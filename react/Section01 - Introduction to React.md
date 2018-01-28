1.Plan of the Course: 
    - Get a boilerplate project
    - Gain famimliarity with React
    - Learn about gengeral data modeling
    - Delve into Redux
3.Modern JS Tooling
    Our prohect files:
        - react
        - redux
        - components
    Through WebPack we transpile it to the html, css, js
4.Environment Setup
    Clone the repository or download zip called ReduxSimpleStarter ar Stephen Grinder profile on GitHub. That will give us base project.
    We have a lot of depencies so we have to do:
        npm install
5.What we will build.        
    That installed our boilerplate project.
    What we are going to build? Before we start learning the React we have to get familiar with React so our first app will be build on it.
    That will be a videoplayer like a YouTube: search, video and the list of videos. We are going to use YouTube API, so it will works.
        npm start
    It will start local server for our project. 
        localhost:8080
    Will open our server.
6. A Taste of JSX.
    Open the code editor. Open index.html
    We have a simple DOM and script bundle.js
    That is our compiled file from the WebPack.
    WebPack compiles all our js files to one file. 
    We have all our code in src folder. Now we will delete and begin from the start. We create 
        index.js 
    file in the src folder. There's no content anymore on the page.
    What is React? React is JS library which is used to produce VIEW! It produce HTMl through components. A component is a collection of JS functions that produces HTML.
    
    In the index.js we create new component which will produce some HTML.
    Then we have to say to React - take this component and put it on the page in HTML.
    
    So, we code:
    ```bash
    const App = function() {
        return <div>Hi!</div>
    }
    ```
7. More on JSX
    No content on our page. We have to put it in the DOM. What is the purpose of JSX? That the JS that produce HTML. So how looks code above in the vanilla JS? It looks something like:
    ```bash 
    React.createElement{
        'div',
        null,
        'Hi!'
    };
    ```
    So it creates the object. It looks ugly so to operate with JSX is much more easier.
8. Rendering components.
    If we React.render(App); still nothing is happening. We have to import react. It's a JS Module that we have to import. 
        import React from 'react';
9. ReactDOM vs React
    We have to use ReactDOM to render component, not React!!!
    To get ReactDOM we have to import it:
        import ReactDOM from 'react-dom';
10/11. ReactDOM.render(<App />, refernceToExistingDomElement)
    When we try to render our component we have to pass to render function which component to render and the place where we want to render it.
    If we write this code:
        const App = () => {
            return <div>Hi!</div>
        }
    What happens? Nothing, it's just a ES6 syntax. It's identical to the using word function.
12. Component Structure
    React app createed from a lot of different components. Every component represents some function. So we have to build an architecture of our applation. We have to spread our app to separate components.
    We will have search cmp, player cmp, video in side-bar cmp, list of that videos cmp, and big component that will be rendered to the html. Building small components help us reuse components where we want. We always make ONLY ONE component per file. In src folder we create new folder components. And also we create files:
        search_bar.js
        video_detail.js
        video_list_item.js
        video_list.js
    This looks like a pretty good file structure. 
13. Youtube Search API Signup
    To fetch data we have to use YouTube API We have to get a key for that. They really want to know who is searching the videos. Let's go to               
        console.developers.google.com
    We have to use our Google Account ot Log In. There are a lot of APIs, we have to find YouTube Data API. At the top there is a button Enable API. On the left menu we click Credentials and then New adn Browser Key. Give it a name and click create. We got an API key which we have to copy. After importing we will create a variable for this key:
        const API_KEY = '__KEY__'
    The next step is to install npm package youtube-search. We will install that with NPM:
        npm i --save youtube-api-search
    --save - saves the package to the package.json file our package.
14. Export Statements
    We will work on the search-bar first. So let's work and open the search-bar.js User types input and we have to do API request.

        import React from 'react';
        
        const SearchBar = () => {
            return <input />
        };

        export default SearchBar
    
    After exporting component we can import it in our main file index.js
        import SearchBar from './components/search_bar'
    Now we can show in index.js our new component.
        const App = () => {
            return (
                <div>
                    <SearchBar />
                </div>
                )
        }
15. Class-based Components.
    If we create component from the function in the variable - that is a functional component. There are also class-components. We are going to create class-based component. Let's go ahead and do the refactoring. We are going to start by writing:
        class SearchBar extends React.Component {
            render() {
                return (

                )
            }
        }
    Every React component has a render method. Now we need only class Component from the React so we have to reassign our React:
        import { Component } from 'react';
16. Handling User Events
    First we have to declare eventHandler. Then we have to pass it to the element that we want. In class SearchBar we define another method. We have to watch onChange in the input of our component so let's call the method onInputMethod. We write in near render method without comma
        onInputChange(event) {

        }
    Now we can pass in attribute (prop) our new method.
        return <input onChange={this.onInputChange}>
    We passed the event or e object to our method. That object describe the informatino about the event. Let's go ahead and write more
        onInputChange(e) {
            console.log(e.target.value);
        }
    Now with Vanilla JS we can see everything we type and change in our console. onChange - it's special property in React. More about that properties we can find in the documentation. target - it's the reference to the element from which we've got our Synthetic Event. Also we can do arrow function in our property:
        <input onChange={e => console.log(e.target.value)}>
17. Introduction to State.
    State is one of the hardest topic in React. Each class has it's own State object. If state is changed render will be rerendered. To initial state we will add new method at the very top:
        constructor(props) {
            super(props);

            this.state = {term: ''}
        }
    Functional components does not have any state. Only class-based components. All JS classes have special function constructor(). In reality this function is called all the time. The constructor is reserved for initializing state. super() - what's that? Reamember that we extend Component. Component itself has constructor function and if we call super() we get state from parent Component. If we dont's call super we will get an error. Whenever we use state we create new object with some properties. Whenever the user updates the search property. As user starts typing we will update our state.
18. Each instance have it's own state. We have record our value to the state. Instead of console.log we will update our state. We really have to know how to manipulate the state. 
         <input onChange={e => this.setState({
             term: e.target.value
         })} />
    Now everytime we change value of our input we change the state of the component and that's why we call our render method again. 
    !!!NEVER DO LIKE THAT: this.state.term = e.target.value
    Always manipulate with this.setState
    So, let's go ahead and refresh.
    We will put our inout in the div
        return (
            <div>
                <input onChange={e => this.setState({
                term: e.target.value
            })} />
                Value of the input: {this.state.term}
            <div />
        )
    Now everything we type is showing. 
19. Controlled Components
    Let's add value to the input.
        <input
            value={this.state.term} 
            onChange={e => this.setState({
                term: e.target.value
            })} />
    This.state causes re-rendering and it changes the value. That retrieves value, so initally it's an empty string. When user enter some text we update to the term and value of input has not actually change. So with writing value we also make value of input to be equal to the new value. Let's say we have some initial value of this.state.term, without value we will not see that there is some data.
20. Breather and Review.
    JSX, Components and State.
    That's the most important topics in React.
    It's near 8% of our Learning. In React there is very small API surface, so that means that understanding of this things allows us to do a lot if things.