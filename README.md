# docker-1
The aim of the Docker-1 project is to make you handle docker and docker-machine, the
bases to understand the idea of containerization of services.

First of all we need to install Homebrew on school's Mac:
```bash
rm -rf $HOME/.brew && git clone --depth=1 https://github.com/Homebrew/brew $HOME/.brew && export PATH=$HOME/.brew/bin:$PATH && brew update && echo "export PATH=$HOME/.brew/bin:$PATH" >> ~/.zshrc
```

Now we are installing docker docker-machine
```bash
brew install docker docker-machine
```
We are moving our Docker to goinfre folder because of limited space:
```bash
mv .docker/ /goinfre/dmukaliy
```
and creating a soft link to it:
```bash
ln -s /goinfre/dmukaliy/.docker $HOME
```

Now we are ready to start exercises.
