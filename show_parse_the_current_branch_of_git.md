# to show parse the current branch of git, add to the .bashrc file

``` bash
function parse_git_branch() {
        BRANCH=`git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\1/'`
        if [ ! "${BRANCH}" == "" ]
        then
                echo "[${BRANCH}${STAT}]"
        else
                echo ""
        fi
}

export PS1="${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\e[0;33m\]\`parse_git_branch\`\[\e[m\]\\$ "
export PATH="~/go/bin:$PATH"
```
