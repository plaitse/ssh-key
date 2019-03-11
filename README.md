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

# JS

- Avoid jQuery: http://youmightnotneedjquery.com/
- To format a string with numbers inside to a  real number, we can add a '+' in front of the variable: ```+string_variable```

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
