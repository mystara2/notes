
here you can find a basic setup for a bash shell, and what the maintainer of this git repo likes to do with their setup.

### **Basic bash setup**

i like to typically have a shell folder in my home folder (~/shellname ex ~/.zsh ~/.bash) with all my configuration instead so i typically do `echo "source ~/.bash/*" > ~/.bashrc` in my bashrc and then do all my configuration in ~/.bash/alias ~/.bash/path and so on.

Basic setup:
```
#!/usr/bin/env bash

# mkdir
mkdir -p ~/.bash
touch ~/.bash/alias ~/.bash/prompt ~/.bash/path ~/.bash/random
echo "source ~/.bash/*" > ~/.bashrc
```

and now i personally like lightweight bash prompts, however in server environments thats not ideal, so i typically do

DIRECTORY
User@hostname$

but if im in a desktop env its

DIRECTORY
`>`