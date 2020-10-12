Quick windows configuration / tips

# Programming and data processing
## git
In Windows 10, installing git is very easy (https://git-scm.com/download/win). 
This will install a shell called `Git Bash`, which is useful as it provides many 
unix shell commands. In windows (git bash shell), do 
```
git config --global core.autocrlf input
```
to convert windows line endings always to linux line endings on commit.

## emacs
Follow the windows section on https://github.com/ctschnur/dotemacs .
## installing linux compatibility tools
### ag
useful for `projectile-ag` and `helm-ag` in emacs. 
Install it using e.g. the windows package manager `chocolatey` (https://chocolatey.org/install#individual) . 
In a powershell terminal with admin rights, type 
```
choco install ag
```
Then, in cmd, show the location of ag: 
```
where ag
```
Add the path to the *front* of your `PATH` environment variable. Restart emacs. 
Now `helm-ag` should work. 

### fzf
Can be installed e.g. in a separate folder `C:/Users/nanospin/misc/fzf/`. 
Emacs will find `fzf.exe`, if this directory is added to `exec-path`. Setting the `PATH` environment variable will also work, after restarting emacs. 

### Testing
- Putting a .emacs in `AppData/Roaming` will load it. -> Checked
- printing `(expand-file-name user-emacs-directory)` in emacs yields
```
"c:/Users/nanospin/AppData/Roaming/.emacs.d/"
```
- printing `(expand-file-name "~")` yields `"c:/Users/nanospin/AppData/Roaming"` 

### python
The error `comint-send-string: Process Python Internal[[some-file.py]]` appears when trying to open any python file `some-file.py`. Probably, `python-mode` wants to 
initialize some things and checks if the command `python` is actually in the `PATH`. If it's not, it throws this error. Usually, I like to install anaconda python on windows 
and then specify the directory of the `base` environment's `python.exe` 
```
C:\Users\nanospin\AppData\Local\Continuum\anaconda3
```
in the account's system variable `PATH`. 

# Dealing with conda environments on windows
Anaconda should install the `Anaconda Prompt`. Inside there, the conda commands
work out-of-the-box: checking out different environments, installing things, etc..

It is useful to add the conda command to the Path variable. Add all directory paths returned by
```
where conda
```
(from anaconda prompt)

to the ~Path~ environment variable. 

# shells in windows
## git bash
If you enjoy working with git, vim and the unix shell, you will probably install this one. 

## cmd
usual windows command line

## Windows PowerShell
looks like cmd, but supports (.Net - type?) scripting. Good (bad) for quickly
installing things from the internet (using ~DownloadString(url)~ function). 
Unlike cmd, it has bck-i-search, with ~Ctrl+R~, which is cool. 

## Anaconda 
When doing data analysis, an anaconda installation can be very useful. It comes with a separate 
prompt for cmd (Anaconda Prompt; shows you the active conda virtual environment) and with a 
PowerShell (PS) prompt.
