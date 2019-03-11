# CSS

- CSS naming: https://spaceninja.com/2018/09/17/what-is-modular-css/
- CSS organization: https://pyx.space/post/keys-to-maintainable-css-order?utm_source=CSS-Weekly&utm_campaign=Issue-336&utm_medium=email

# Docker

Docker is a solution to run software packages called containers which are isolated from each other and bundle their own application, tools, librairies and configuration files. They can communicate with each other through well-defined channels. Containers are created from images that specify their precise contents.

Here are its benefits:
- Reproducibility: Similar to a Java application, which will run exactly the same on any device capable of running a Java Virtual Machine, a Docker container is guaranteed to be identical on any system that can run Docker. The exact specifications of a container are stored in a Dockerfile. By distributing this file among team members, an organization can guarantee that all images built from the same Dockerfile will function identically.
- Isolation: Dependencies or settings within a container will not affect any installations or configurations on your computer, or on any other containers that may be running. By using separate containers for each component of an application (for example a web server, front end, and database for hosting a web site), you can avoid conflicting dependencies. You can also have multiple projects on a single server without worrying about creating conflicts on your system.
- Security: Separating the different components of a large application into different containers can have security benefits: if one container is compromised the others remain unaffected.
- Environment Management: Docker makes it easy to maintain different versions of, for example, a website using nginx. You can have a separate container for testing, development, and production on the same Linode and easily deploy to each one.
- Continuous Integration: Docker works well as part of continuous integration pipelines with tools like Travis, Jenkins, etc. Every time your source code is updated, these tools can save the new version as a Docker image, tag it with a version number and push to Docker Hub, then deploy it to production.

# DOM

The Document Object Model (DOM) is an application programming interface (API) for valid HTML and well-formed XML documents. It defines the logical structure of documents and the way a document is accessed and manipulated. Almost anything found in an HTML or XML document can be accessed, changed, deleted, or added. The DOM originated as a specification to allow JavaScript scripts and Java programs to be portable among Web browsers.

In the DOM, documents have a logical structure which is very much like a tree; to be more precise, which is like a "forest" or "grove", which can contain more than one tree. Each document contains zero or one doctype nodes, one root element node, and zero or more comments or processing instructions; the root element serves as the root of the element tree for the document.

The name "Document Object Model" was chosen because it is an "object model" in the traditional object oriented design sense: documents are modeled using objects, and the model encompasses not only the structure of a document, but also the behavior of a document and the objects of which it is composed. In other words, the nodes in the above diagram do not represent a data structure, they represent objects, which have functions and identity.

# JS

- Avoid jQuery: http://youmightnotneedjquery.com/
- To format a string with numbers inside a real number, we can add a '+' in front of the variable: ```+string_variable```

## Asynchronous

JavaScript is a single threaded language (aside service workers) so every code is being run as a single JavaScript process in the computer.

For the most part, JavaScript is a synchronous procedural code read from top to bottom. However, it can also run code in an asynchronous way (e.g. setTimeout, callbacks, promises, fetch, ajax, filesystem interaction, database calls, DOM listeners...). This code is set aside in a queue and will be executed after the synchronous one.

![alt text](/asynchronous.jpeg)

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

# Metadata

Meta elements are used to specify page description, keywords, author of the document, last modified, etc. This data can be used by browsers (how to display content or reload page), search engines (keywords) or other web services.

To define keywords for search engines:
```<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">```

To define a description of your web page:
```<meta name="description" content="Free Web tutorials on HTML and CSS">```

To define the author of a page:
```<meta name="author" content="John Doe">```

To refresh document every 30 seconds:
```<meta http-equiv="refresh" content="30">```

To set the viewport to make your website look good on all devices:
```<meta name="viewport" content="width=device-width, initial-scale=1.0">```

Others:
- ```charset```: specifies the character encoding for the HTML document.
- ```content```: gives the value associated with the http-equiv or name attribute.
- ```http-equiv```: provides an HTTP header for the information/value of the content attribute.

# SASS

Sass is a preprocessor scripting language that is interpreted or compiled into CSS. Sass consists of two syntaxes. It uses indentation to separate code blocks and newline characters to separate rules. The newer syntax, "SCSS" (Sassy CSS), uses block formatting like that of CSS. It uses braces to denote code blocks and semicolons to separate lines within a block. SassScript, the scripting language, provides mechanisms like variables, nesting, mixins, and selector inheritance.

# SSH

## Create a GitHub SSH key without error

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
