# Create a GitHub SSH key without error

## First, paste the text below, substituting in your GitHub email address:
```ssh-keygen -t rsa -b 4096 -C "your_email@example.com"```

## Then, start the ssh-agent in the background:
```eval "$(ssh-agent -s)"```

## Then, create or modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain:
```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

## Then, add your SSH private key to the ssh-agent and store your passphrase in the keychain:
```ssh-add -K ~/.ssh/id_rsa```

## Finaly, add the SSH key to your GitHub account.
