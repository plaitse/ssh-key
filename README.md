CSS
- Box Sizing
- Naming
- Organization
- SASS

Docker
- Reproducibility
- Isolation
- Security
- Environment Management
- Continuous Integration

GitHub
- SSH Key
- Language of the repository

HTML
- DOM
- Metadata
- Semantic

JavaScript
- Asynchronous
- Conventions
--- Naming
--- OOP design
--- Testing
- Immutability
--- Pass by value
--- Pass by reference
- Promise
- <script> tag in HTML
--- async
--- defer
- Rest operator
- Splice and filter
- Spread operator
- Storage
--- Cookie
--- LocalStorage
--- SessionStorage
--- Good practice
- Testing
--- Unit testing
--- Integration testing
--- Functional testing
--- TDD
- Webpack

---

# CSS

## Box sizing

By default:
```html
width + padding + border = actual width of an element
height + padding + border = actual height of an element
```

The ```box-sizing``` property allows us to include the padding and border in an elemen'ts total width and height instead of the default behavior which will increase the element's size. That way we keep each element the width and height we assigned to them.

## Naming

https://spaceninja.com/2018/09/17/what-is-modular-css/

## Organization

https://pyx.space/post/keys-to-maintainable-css-order?utm_source=CSS-Weekly&utm_campaign=Issue-336&utm_medium=email

## SASS

Sass is a preprocessor scripting language that is interpreted or compiled into CSS. It consists of two syntaxes. First, it uses indentation to separate code blocks and newline characters to separate rules. Second, the newer syntax, "SCSS" (Sassy CSS), uses block formatting like that of CSS. It uses braces to denote code blocks and semicolons to separate lines within a block. SassScript, the scripting language, provides mechanisms like variables, nesting, mixins, and selector inheritance.

# Docker

Docker is a solution to run software packages called containers which are isolated from each other and bundle their own application, tools, librairies and configuration files. They can communicate with each other through well-defined channels. Containers are created from images that specify their precise contents.

Here are its benefits:

## Reproducibility

Similar to a Java application, which will run exactly the same on any device capable of running a Java Virtual Machine, a Docker container is guaranteed to be identical on any system that can run Docker. The exact specifications of a container are stored in a Dockerfile. By distributing this file among team members, an organization can guarantee that all images built from the same Dockerfile will function identically.

## Isolation

Dependencies or settings within a container will not affect any installations or configurations on your computer, or on any other containers that may be running. By using separate containers for each component of an application (for example a web server, front end, and database for hosting a web site), you can avoid conflicting dependencies. You can also have multiple projects on a single server without worrying about creating conflicts on your system.

## Security

Separating the different components of a large application into different containers can have security benefits: if one container is compromised the others remain unaffected.

## Environment Management

Docker makes it easy to maintain different versions of, for example, a website using nginx. You can have a separate container for testing, development, and production on the same Linode and easily deploy to each one.

## Continuous Integration

Docker works well as part of continuous integration pipelines with tools like Travis, Jenkins, etc. Every time your source code is updated, these tools can save the new version as a Docker image, tag it with a version number and push to Docker Hub, then deploy it to production.

# GitHub

## SSH key

- First, paste the text below, substituting in your GitHub email address:
```ssh-keygen -t rsa -b 4096 -C "your_email@example.com"```

- Then, start the ssh-agent in the background:
```eval "$(ssh-agent -s)"```

- Then, create or modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain:
```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

- Then, add your SSH private key to the ssh-agent and store your passphrase in the keychain:
```ssh-add -K ~/.ssh/id_rsa```

- Finaly, add the SSH key to your GitHub account.

## Language of the repository

If I want my repository to be recognized as a VueJS project by GitHub, I need to set a .gitattributes file at the root of my project which contains:

```js
* linguist-vendored // Remove every file from GitHub statistics
*.vue linguist-vendored=false // Keep these files for statistics
```

# HTML

## DOM

The Document Object Model (DOM) is an application programming interface (API) for valid HTML and well-formed XML documents. It defines the logical structure of documents and the way a document is accessed and manipulated. Almost anything found in an HTML or XML document can be accessed, changed, deleted, or added. The DOM originated as a specification to allow JavaScript scripts and Java programs to be portable among Web browsers.

In the DOM, documents have a logical structure which is very much like a tree; to be more precise, which is like a "forest" or "grove", which can contain more than one tree. Each document contains zero or one doctype nodes, one root element node, and zero or more comments or processing instructions; the root element serves as the root of the element tree for the document.

The name "Document Object Model" was chosen because it is an "object model" in the traditional object oriented design sense: documents are modeled using objects, and the model encompasses not only the structure of a document, but also the behavior of a document and the objects of which it is composed. In other words, the nodes in the above diagram do not represent a data structure, they represent objects, which have functions and identity.

## Metadata

Meta elements are used to specify page description, keywords, author of the document, last modified, etc. This data can be used by browsers (how to display content or reload page), search engines (keywords) or other web services.

- To define keywords for search engines:
```<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">```
- To define a description of your web page:
```<meta name="description" content="Free Web tutorials on HTML and CSS">```
- To define the author of a page:
```<meta name="author" content="John Doe">```
- To refresh document every 30 seconds:
```<meta http-equiv="refresh" content="30">```
- To set the viewport to make your website look good on all devices:
```<meta name="viewport" content="width=device-width, initial-scale=1.0">```

Others:
- ```charset```: specifies the character encoding for the HTML document.
- ```content```: gives the value associated with the http-equiv or name attribute.
- ```http-equiv```: provides an HTTP header for the information/value of the content attribute.

## Semantic

Semantic elements make it easier for search engines to identify the correct web page content.

Many web sites contain HTML code like: ```<div id="nav">``` or ```<div class="header">``` to indicate navigation, header, footer, etc. HTML5 offers new semantic elements to define different parts of a web page:
- ```<article>``` : defines an article.
- ```<aside>``` : defines content aside from the page content like a sidebar.
- ```<details>``` : defines additional details that the user can view or hide.
- ```<em>``` : defines italic text to emphasize it and semantic importance (whereas ```<i>``` text has no importance).
- ```<figure>``` : specifies self-contained content, like illustrations, diagrams, photos, code listings, etc.
- ```<figcaption>``` : defines a caption (visual explanation) for a ```<figure>``` element.

```html
<figure>
  <img src="image.jpg" alt="What's the image about">
  <figcaption>Fig1. - Caption.</figcaption>
</figure>
```

- ```<header>``` and ```<footer>``` : specifies a header and a footer for a document or section.
- ```<header>``` : specifies a header for a document or section. We can have several ```<header>``` and ```<footer>``` elements in one document.

```html
<article>
  <header>
    <h1>Title of the article</h1>
    <p>Sub information</p>
  </header>
  <p>Body content of the article</p>
</article>
```

- ```<main>``` : specifies the main content of a document.
- ```<mark>``` : specifies marked/highlighted text.
- ```<nav>``` : defines a set of navigation links.

```html
<nav>
  <a href="/html/">HTML</a> |
  <a href="/css/">CSS</a> |
  <a href="/js/">JavaScript</a> |
  <a href="/jquery/">jQuery</a>
</nav>
```

- ```<section>``` : defines a section in a document.
- ```<strong>``` : defines bold text with semantic importance (whereas ```<b>``` text has no importance).
- ```<summary>``` : defines a visible heading for a ```<details>``` element.
- ```<time>``` : defines a date/time.

![alt text](/semantic.png)

![alt text](/semantic2.jpg)

![alt text](/semantic3.png)

# JavaScript

- Avoid jQuery: http://youmightnotneedjquery.com/
- To format a string with numbers inside a real number, we can add a '+' in front of the variable: ```+string_variable```

## Asynchronous

JavaScript is a single threaded language (aside service workers) so every code is being run as a single JavaScript process in the computer.

For the most part, JavaScript is a synchronous procedural code read from top to bottom. However, it can also run code in an asynchronous way (e.g. setTimeout, callbacks, promises, fetch, ajax, filesystem interaction, database calls, DOM listeners...). This code is set aside in a queue and will be executed after the synchronous one.

![alt text](/asynchronous.jpeg)

## Conventions

### Naming

- All of the types (classes, enums, interfaces) must follow _PascalCase_ convention
- Vue (dom) component names must follow _kebab-case_ convention
- Variables and functions must follow _camelCase_ convention
- Interfaces names should start with **I** for convenience
- main for libraries should be (index.js or index.ts)
- main for microservices should be (server.js or server.ts)
- Avoid enums with numerical values when possible (except for binary flags case) and explicitely assign string values to them

### OOP design

- Avoid writing functions with more than 3 parameters, if there is a need for, pass a "context" object with all of those
- Follow the [SOLID](https://en.wikipedia.org/wiki/SOLID) object oriented design principles, keep your classes and methods as small as possible.
- Keep it simple! Avoid complicated patterns when not necessary
- Entities destined to be persisted into a storage (Mongo, Couch, Mariadb etc ..) must be modeled as classes with a default values for each property
- Write comments when needed on classes and identifiers (methods, properties, parameters, contructors)

### Testing

- Do a clear separation between end-to-end/integration testing and unit tests: unit tests don't launch a program, don't do network of file system access. Integration and end-to-end (browser testing) are considered the same. **unit test files must end with .test.js**, **end-to-end and integration test files names must end with .e2e.js**. Keep in mind that those tests will not run in the same Gitlab CI pipeline.

## Immutability

Mutation is anything that changes/transforms the behavior or the structure of an object.

### Pass by value

```js
let a = 1;
let b = a;

console.log(a); // 1
console.log(b); // 1

a = 10;
console.log(a); // 10
console.log(b); // 1
```

### Pass by reference

```js
// Objects
let object1 = {name: 'test'};
let object2 = object1;

console.log(object1); // {name: 'test'}
console.log(object2); // {name: 'test'}

object1.name = 'toast';

console.log(object1); // {name: 'toast'}
console.log(object2); // {name: 'toast'}

// Arrays
let arr = [1,2,3,4,5];
let newArr = arr;

console.log(arr); // [1,2,3,4,5]
console.log(newArr); // [1,2,3,4,5]

arr.push(6);

console.log(arr); // [1,2,3,4,5,6]
console.log(newArr); // [1,2,3,4,5,6]
```

Objects and arrays are usually passed by reference. Since object2 is equated to object1, it is passed by reference, meaning, they both hold the same memory location. So, when we change the value of object1, object2 usually gets changed.

![alt text](/reference.png)

This means if you pass an object/array across various functions, and you mutate it at some point, the same object/array might be mutated in other places, leading to unexpected behavior in some parts of the code, resulting in bugs.

One way of achieving immutability in JavaScript is by using Object.assign:

```js
let object1 = {name: 'test'};
let object2 = Object.assign({}, object1, {name: 'toast'});

console.log(object1); // {name: 'test'}
console.log(object2); // {name: 'toast'}

object1.name = 'trust';

console.log(object1); // {name: 'trust'}
console.log(object2); // {name: 'toast'}
```

Another way is by using the spread operator:

```js
// Objects
let object1 = {name: 'test'};
let object2 = {...object1, name: 'toast'};

console.log(object1); // {name: 'test'}
console.log(object2); // {name: 'toast'}

object1.name = 'trust';

console.log(object1); // {name: 'trust'}
console.log(object2); // {name: 'toast'}

// Arrays
let arr = [1,2,3,4,5];
let newArr = [...arr, 6];

console.log(arr); // [1,2,3,4,5]
console.log(newArr); // [1,2,3,4,5,6]

arr.push(11);

console.log(arr); // [1,2,3,4,5,11]
console.log(newArr); // [1,2,3,4,5,6]
```

Also, for arrays in JavaScript, ```map, filter, reduce``` can be used to avoid mutations since they return new arrays every-time they are called.

## Promise

The promise objet represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.

```js
var promise1 = new Promise(function(resolve, reject) {
  setTimeout(function() {
    resolve('test');
  }, 300);
});

promise1.then(function(value) {
  console.log(value);
  // expected output: "test"
});

console.log(promise1);
// expected output: [object Promise]
```

## ```<script>``` tag in HTML

The best practice is to put scripts in the ```<head>``` tag and use the ```async``` or ```defer``` attributes to allow these scripts to be downloaded as soon and as fast as possible without blocking the browser parsing the HTML.

### async

```js
<script type="text/javascript" src="path/to/script1.js" async></script>
<script type="text/javascript" src="path/to/script2.js" async></script>
```

Scripts with the ```async``` attribute are executed asynchronously. They are executed as soon as they are downloaded without blocking the browser. Be aware, script 2 could potentially be downloaded and executed before script 1.

### defer

```js
<script type="text/javascript" src="path/to/script1.js" defer></script>
<script type="text/javascript" src="path/to/script2.js" defer></script>
```

Scripts are executed in order and do not block the browser. Unlike ```async``` scripts, defer ones are only executed after the entire document has been loaded.

## Rest operator

Takes several values and turns them in on array:
```js
function makeArray(name: string, ...args: number[]) {
  return args;
}
console.log(makeArray("Che", 1, 2, 15)); // [1, 2, 15]
```

## Splice and filter

```js
const id = 2;
const newArray = [...state.results];
newArray.splice(id, 1);
```

is equivalent to:

```js
const newArray = state.results.filter(result => result.id !== id);
```

## Spread operator

To keep the state immutable:

```js
const newState = Object.assign({}, state);
newState.counter = state.counter + 1;
return newState;
```

is equivalent to:

```js
return {
  ...state,
  counter: state.counter + 1
}
```

## Storage

![alt text](/storage.png)

### Cookie

Before HTML5, information on the app could only be saved through cookies.

- Stores data that has to be sent back to the server with subsequent requests. Its expiration varies based on the type and the expiration duration can be set from either server-side or client-side (normally from server-side).
- Primarily for server-side reading but can also be read on client-side.
- Can be made secure by setting the httpOnly flag as true for that cookie. This prevents client-side access to that cookie.
- Can only store strings.
- We cannot get one cookie at a time, all the cookies get stored in one string file. As we get them all at once when requested, we need to parse them to target a specific one.

To set, get and remove one:
```js
document.cookie = "id=123"; // No experiation date
document.cookie = "id=123; expires=Fri, 31 Dec 2020 23:59:59 GMT"; // Will expire
console.log(document.cookie);
document.cookie = "id=; expires=Fri, 31 Dec 1970 00:00:00 UTC"; // To remove one
```

### LocalStorage

- Stores data with no expiration date, and gets cleared only through JavaScript, or clearing the Browser cache / Locally Stored Data
- Can store variables but not arrays neither objects.
- Can only be read on client-side.

To set, get and remove one:
```js
localStorage.setItem('id'; '123');
console.log(localStorage.getItem('id'));
localStorage.removeItem('id'); // Remove a single one
localStorage.clear(); // Remove all
```

### SessionStorage

- Stores data only for a session, meaning that the data is stored until the browser (or tab) is closed.
- Data is never transferred to the server.
- Can store variables but not arrays neither objects.
- Can only be read on client-side.

To set, get and remove one:
```js
sessionStorage.setItem('id'; '123');
console.log(sessionStorage.getItem('id'));
sessionStorage.removeItem('id'); // Remove a single one
sessionStorage.clear(); // Remove all
```

### Good practice

Passwords or other sensible information shouldn't be stored on client-side but only on the server's session. The most common thing is store tokkens on the client-side therefore we need the server's session should bet set to expire after a certain amount of time to avoid consuming ressources.

## Testing

Testing should be present all the time, by applying test-driven development.

### Unit testing

Unit testing is the practice of testing small pieces of code, typically individual functions, alone and isolated. If your test uses some external resource, like the network or a database, it’s not a unit test. It should essentially just give the function that’s tested some inputs, and then check what the function outputs is correct.

Tools: Mocha, Jest, Jasmine and Tape.

### Integration testing

The idea is to test how parts of the system work together - the integration of the parts. While unit tests are isolated from other components, integration tests are not. For example, a unit test for database access code would not talk to a real database but an integration test would. One test could be validating a database by querying it to check the state is correct.

Integration tests is more complex than unit ones because they might need some set up or configuration such as the setting up of a test database. Thefore we should only use them if necessary, when a piece of code is too complex to unit test.

Tools: Mocha, Jest, Jasmine and Tape.

### Functional aka E2E aka browser aka acceptance testing

Functional testing is defined as the testing of complete functionality of some application; in practice with web apps, this means using some tool to automate a browser, which is then used to click around on the pages to test the application.

Functional tests should be used for testing common user interactions to test a certain flow in a browser, such as registering an account.

As integration tests, functional ones are complex and should be limited. They also run very slowly because they simulate real user interaction on a web page, so even page load times become a factor.

While in unit and integration tests we would validate the results in code, functional test results should be validated the same way as if we were a user of the page. For instance, we could validate by checking that the browser is redirected to a "thanks for registering page".

Tools: Selenium, Nightwatch, Protactor, PhantomJS and CasperJS.

### TDD

Test-Driven Development is a process for when we write and run tests. Following it makes it possible to have a very high test-coverage which is the percentage of code that is tested automatically.

It consists of the following tests:
- Start by writing a test.
- Run the test and any other tests. At this point, the newly added test should fail. If it doesn't fail here, it might not be testing the right thing and thus has a bug in it.
- Write the minimum amount of code required to make the test pass.
- Run the tests to check the new test passes.
- Optionally refactor the code.
- Repeat from 1.

## Webpack

Webpack is a JavaScript module bundler capable of transformating, bundling or packaging any resource or asset like JavaScript, HTML, CSS and images if the corresponding plugins are included. It allows a modular approach for the application development.

Famous features:
- The bundler can be configured using a config file named webpack.config.js.
- It can take modules with dependencies and generates static assets representing those modules.
- Loaders allow to write custom tasks that we want to perform when bundling files together.
- Provides a built in development server called Webpack Dev Server that can be used as a HTTP server for serving our files. 
- Provides the capability to use Hot module replacement by turning on the hot flag.

Createapp.dev simplifies the process of creating the config file: https://createapp.dev/webpack.
