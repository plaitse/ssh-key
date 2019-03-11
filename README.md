# CSS

- CSS naming: https://spaceninja.com/2018/09/17/what-is-modular-css/
- CSS organization: https://pyx.space/post/keys-to-maintainable-css-order?utm_source=CSS-Weekly&utm_campaign=Issue-336&utm_medium=email

# JS

- Avoid jQuery: http://youmightnotneedjquery.com/
- To format a string with numbers inside to a  real number, we can add a '+' in front of the variable: ```+string_variable```

## ```<script>``` tag in HTML

The best practice is to put scripts in the ```<head>``` tag and use the async or defer attributes to allow these scripts to be downloaded as soon and as fast as possible without blocking the browser parsing the HTML.

### async

```js
<script type="text/javascript" src="path/to/script1.js" async></script>
<script type="text/javascript" src="path/to/script2.js" async></script>
```

Scripts with the async attribute are executed asynchronously. They are executed as soon as they are downloaded without blocking the browser. Be aware, script 2 could potentially be downloaded and executed before script 1.

### defer

```js
<script type="text/javascript" src="path/to/script1.js" defer></script>
<script type="text/javascript" src="path/to/script2.js" defer></script>
```

Scripts are executed in order and do not block the browser. Unlike async scripts, defer ones are only executed after the entire document has been loaded.

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
