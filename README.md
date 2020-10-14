<<<<<<< HEAD

Quick windows configuration / tips
=======
# Setting up windows
>>>>>>> 4daa59aa90cc5889d4bef23822baf7d4c1ad3751

## Essentials
### python
Add an independent python installation to your system (e.g. from https://www.python.org/downloads/windows), a version that is stable enough (not necessarily the newest) for e.g. your emacs installation. When calling `where python.exe` from a plain `cmd.exe` (not anaconda prompt), the installation path should be the first that appears (after having added it to `PATH`). 

## Programming and data processing
### git
In Windows 10, installing git is very easy (https://git-scm.com/download/win). 
This will install a shell called `Git Bash`, which is useful as it provides many 
unix shell commands. In windows (git bash shell), do 
```
git config --global core.autocrlf input
```
to convert windows line endings always to linux line endings on commit.

### emacs
Follow the windows section on https://github.com/ctschnur/dotemacs .

### anaconda 
[Install](https://docs.anaconda.com/anaconda/install/windows/) it. 

#### dealing with conda environments on windows
Anaconda should install the `Anaconda Prompt`. Inside there, the conda commands
work out-of-the-box: checking out different environments, installing things, etc..
It can be useful to add the conda command to the Path variable. Add all directory paths returned by `where conda` (from anaconda prompt) to the `Path` environment variable. 

### compatibility tools from unix
#### ag
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

#### fzf
Can be installed e.g. in a separate folder `C:/Users/nanospin/misc/fzf/`. 
Emacs will find `fzf.exe`, if this directory is added to `exec-path`. Setting the `PATH` environment variable will also work, after restarting emacs. 

#### diff
Can be installed using the windows package manager `scoop` (package manager for people familiar with Unix tools).

## shells on windows
### git bash
If you enjoy working with git, vim and the unix shell, you will probably install this one. 

### cmd
usual windows command line

### Windows PowerShell
looks like cmd, but supports (.Net - type?) scripting. Good (bad) for quickly
installing things from the internet (using ~DownloadString(url)~ function). 
Unlike cmd, it has bck-i-search, with ~Ctrl+R~, which is cool. 

### Anaconda PowerShell and Anaconda Prompt
When doing data analysis, an anaconda installation can be very useful. It comes with a separate 
prompt for cmd (Anaconda Prompt; shows you the active conda virtual environment) and with a 
PowerShell (PS) prompt. 

## package managers on windows
### Scoop
Install it by running the instructions at https://scoop.sh/ in a windows PowerShell 
(installation into a local account: don't run PowerShell as Administrator). 
This should automatically add an entry of scoop's binary folder your `PATH`.
