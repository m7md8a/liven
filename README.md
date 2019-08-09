## Active js
A scalable Frontend Javascript framework for high performance and flexibility for building solid Single Page Apps

### Use Cases
1. You can use this framework to build small single page apps
2. You can use this framework to build scalable and large single page apps

### Features
1. Components based
2. zero time to start your development process
3. no need for webpack or any module bundler
4. Scalable Framework which allows you to build any type of single page apps
5. Uses Javascript Es6 code syntax and class concept
   Uses Javascript Proxy for real time dom updates
6. Solid Routing System
7. Dom Updating without emitting any functions to change the DOM
8. Isolated components and Data Model for every component
9. Writing isolated HTML component and JS component or writing them together in the same file

### Getting Started
#### Example
```javascript
import {Active, Component} from "Active.js"

class HomeComponent extends Component{

    constructor(props) {
        super(props);

        // define data
        
        this.$store.message = "hello";
        
        this.$store.frameWork = "Activejs"
        
        // init the component on instantiate
        this.init();
    }
    render() {
    
    return `<div class="component">
            <h1>{{message}} {{frameWork}}</h1>
        </div>`
    
    }
}
// instantiate the home component class
const home = new HomeComponent({

    // define the parent element

    parent: ".app",
    uniqueName: "homeComponent"
})
```
#### Content
- [installing](#installing)

#### installing
```
npm install activejs
```

#### Components
Activejs is build upon component concept, it divides the web page into components and every component can contain many and many small components inside it and every component is isolated with specific data model which is active along the time and reflects dom changes once you change the data of that component

Activejs uses Javascript Es6 classes to extend Activejs component class to your own custom components
Activejs uses native html elements without shadow root or web components to give you best performance and SEO optimization

**Example**
```javascript
import {Active, Component} from "Active.js"

class HomeComponent extends Component{

    constructor(props) {
        super(props);

        // define data
        
        this.$store.message = "hello";
        
        this.$store.frameWork = "Activejs"
        
        // init the component on instantiate
        this.init();
    }
    render() {
    
    return `<div class="component">
            <h1>{{message}} {{frameWork}}</h1>
        </div>`
    
    }
```

to create your first Activejs Component you need to import Activejs and Component classes from Activejs as the following:

```javascript
import {Active, Component} from "Active.js"
```
Now to write your own component you need to extend a class from Component class like the following

```javascript
class Header extends Component{
    // call constructor
    constructor(props) {
        super(props);
    }
}
```

Every component should have some props as setting object for this component and you should pass these props to the super class as the above example

Maybe type are asking now how will you write html content inside Js file !!!

You have two options to write component html content as the following

- write html elements as string inside render function in component class
- write html content in separated html file

##### Write HTML content inside Activejs Component file
```javascript
class Header extends Component{
    // call constructor
    constructor(props) {
        super(props);
    }
    // render method to render html content
    render() {
        return `
            <header>
                <nav>
                    <h1>Header Component</h1>
                </nav>
            </header>
        `
    }
}
```
Until now Activejs component will not be working because you need two things:
1. create a parent element in html page to put this component inside it
2. instantiate this component and init it


Now create html file called ``index.html``

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Activejs Example</title>
</head>

<body>
    <!-- header component -->
    <div class="header"></div>
    <h1>page</h1>
    <script type="module" src="/app.js"></script>
</body>
</html>
```
Now you need to instance ``Header`` component that you have created and initialize it
```javascript
const header = new Heder({
    parent: document.querySelector(".header")
});
```
When you instantiate a new component there are some configuration and settings you can set to that component, some of these settings are mandatory and others are optional

#### component ``props`` object
|key |description |value |required |type |
|-|-|-|-|-|
|parent|the html parent that you want to assign this component to it|document.querySelector or string|true|dom element or string |
|uniqueName|a unique name or id you assign to this component |componentName|true|string |
|animate |animation you want to add to the component when it initialized |Object |false | Object|
|fadeIn |fadeIn animation you want to add to the component when it initialized |Object |false | Object|
|slideDown |slideDown animation you want to add to the component when it initialized |Object |false | Object|

**initialize Activejs Component**
```javascript
header.init();
```
This function make initialization to the component, also you can make the component auto initialized when you instance a new component like the following
```javascript
class Header extends Component{
    // call constructor
    constructor(props) {
        super(props);
        // initialize the component
        this.init();
    }
    // render method to render html content
    render() {
        return `
            <header>
                <nav>
                    <h1>Header Component</h1>
                </nav>
            </header>
        `
    }
}
const header = new Heder({
    parent: document.querySelector(".header")
});
```
