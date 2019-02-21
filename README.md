# CSS

- CSS naming: https://spaceninja.com/2018/09/17/what-is-modular-css/
- CSS organization: https://pyx.space/post/keys-to-maintainable-css-order?utm_source=CSS-Weekly&utm_campaign=Issue-336&utm_medium=email

# JS

- Avoid jQuery: http://youmightnotneedjquery.com/
- To format a string with numbers inside to a  real number, we can add a '+' in front of the variable: ```+string_variable```

## Spread operator

```const newState = Object.assign({}, state);
newState.counter = state.counter + 1;
return newState;```

est équivalent à :

```return {
  ...state,
  counter: state.counter + 1
}```

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
