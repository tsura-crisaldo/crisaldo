# Can't use "conda", "pip" command and can't find python3 through Terminal on Mac

Today when I try to use pip, conda through terminal, I found it showed me like this:
`pip: command not found` and `conda: command not found`.

1. I tried to use the easiest way to solve this: reinstall anaconda3.

    I should **uninstall anaconda3** first:
   - using [App Cleaner](https://nektony.com/mac-app-cleaner) to unistall anaconda-navigator and some remaining files.
   - deleting anaconda3 dictionary through its path **i.e. /User/myUserID/opt/anaconda3**.
   - deleting lines about anaconda3 **(Ctrl+U)** in .bash_profile file, the difference among /etc/profile, ~/.bashrc, and ~/.bash_profile: [Chinese](https://zhuanlan.zhihu.com/p/25944849) or [English](https://www.stefaanlippens.net/bashrc_and_others/).
   - redownloading [anaconda](https://www.anaconda.com/distribution/) and installing.
   
    It doesn't work at here, but sometimes it does 

2. I found python3 still in my computer but I can only find python2 through terminal, then I found all of the python3 files are in the `/bin` dictionary in my anaconda3 installation path `/Users/myUserID/opt/anaconda3/bin`, so I guess `/bin` dictionary in anaconda3 contains all of the python3 files and I didn't set the right `PATH`, so my system couldn't find the right `PATH` to launch python3 when I input `python3` into terminal, and that's why `conda` and `pip` are also not found, since `/bin` dictionary in anaconda3 contains all of these related things. 

    **set right `PATH` for my shell to find application**:
   - open ~/.zshrc file: `vim ~/.zshrc`(I use zshell so here I edit ~/.zshrc file, normally you use bash, because it's default set, so you just need to edit ~/.bashrc file: `vim ~/.bashrc`).
   - `i` to start editing file, inserting `export PATH="$PATH:/User/myUserID/opt/anaconda3/bin"` to this file(This is to tell the shell where to find all the command contained in anaconda3), then `:`, finally `wq` to save and exit.
   - restart terminal, I found all the commands like `conda` and `pip` can use now.
`
