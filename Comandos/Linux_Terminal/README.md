# Terminal de Linux

Personalización de mi terminal.

```bash
# Comentario al abrir la terminal

echo -e "\033[0;35m ¡Bienvenido, Diego!"

# Aliases

alias profile="nano ~/.bash_profile" o "nano ~/.bashrc"
alias sprofile="source ~/.bash_profile"
alias gita="git add --all"
alias gitc="git commit -m"
alias gitp="git push"
alias gits="git status"
alias gitb="git branch"
alias gith="git checkout"
alias jl="python3 -m jupyterlab"
alias e="exit"
alias hib="sudo hibernate"
alias r="ruby"
alias psql="sudo su - postgres"


# Personalización Prompt

parse_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u\[\033[00m\] \[\033[01;34m\]\W\[\033[01;36m\]$(parse_branch) \[\033[00m\]>> '
else
    PS1='${debian_chroot:+($debian_chroot)}\u \W >> '
fi
```

## Prompt personalizado:

El prompt consiste en toda la parte previa al input en la terminal del sistema operativo. En este caso está el usuario del sistema operativo (verde claro), seguido por la carpeta donde se ejecuta la terminal (azul obscuro), luego la branch actual entre paréntesis (celeste) y finalmente el símbolo que indica dónde escribir (blanco). La marca de la branch aparece siempre y cuando se esté dentro de un repositorio de git. 


![Pantallazo de una terminal de linux con el prompt personalizado](https://raw.githubusercontent.com/DiegoEmilio01/Programs-Storage/master/Assets/promt_linux.png "Terminal personalizada")
