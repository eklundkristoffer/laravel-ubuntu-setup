1. Generate a deploy key on the server. Use app-level specific keys. [See more](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux)
```bash
ssh-keygen -t ed25519 -C "myapp-deploy-key"

# > Enter file in which to save the key (/home/ubuntu/.ssh/id_ed25519):
/home/ubuntu/.ssh/myapp-deploy-key

eval "$(ssh-agent -s)"

ssh-add /home/ubuntu/.ssh/myapp-deploy-key
```

2. Add the public key to github deploy keys
```bash
cat /home/ubuntu/.ssh/myapp-deploy-key.pub
```
