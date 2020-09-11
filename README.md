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
The init file is first read from the location of the environment variable HOME (https://www.gnu.org/software/emacs/manual/html_node/efaq-w32/Location-of-init-file.html). 
Check the value of this environment variable using
```
echo %HOME%
```
If it's not set, you can edit the local account environment variables and check again. 

If %HOME% doesn't exist, emacs looks in the `AppData` directory. There you can put a file ~.emacs~ 
which just loads the actual ~init.el~, 
```
(message "hi from AppData/Roaming")
(load "c:/Users/nanospin/misc/dotemacs/.emacs.d/init.el")
```
within which you set your ~user-emacs-directory~ to your dotemacs repo's ~.emacs.d/~ folder. 

## installing linux compatibility tools
### ag
useful for ~projectile-ag~ and ~helm-ag~ in emacs. 
Install it using e.g. the windows package manager `chocolatey` (https://chocolatey.org/install#individual) . 
In a powershell terminal with admin rights, type 
```
choco install ag
```
Then, in cmd, show the location of ag: 
```
where ag
```
Add the path to the *front* of your ~Path~ environment variable. Restart emacs. 
Now ~helm-ag~ should work. 


### fzf
Can be installed e.g. in a separate folder ~C:/Users/nanospin/misc/fzf/~. 
Emacs will find ~fzf.exe~, if this directory is added to ~exec-path~. 

### Testing
- Putting a .emacs in `AppData/Roaming` will load it. -> Checked
- printing `(expand-file-name user-emacs-directory)` in emacs yields
```
"c:/Users/nanospin/AppData/Roaming/.emacs.d/"
```
- printing `(expand-file-name "~")` yields `"c:/Users/nanospin/AppData/Roaming"` 


### one proposed option to integrate: 
```
;; Place this file in C:\Users\Username\AppData\Roaming and point to the appropriate files
(setq user-init-file "C:/path/to/.emacs")
(setq user-emacs-directory "C:/path/to/.emacs.d/")
(setq default-directory "C:/whatever/you/want/to/start/in")
(setenv "HOME" "D:/my/home/directory")
(load user-init-file)
```
(see https://emacs.stackexchange.com/questions/12881/how-do-i-set-a-different-location-for-the-dot-emacs-emacs-file-on-windows-7/12886#12886)

# Dealing with conda environments on windows
Anaconda should install the `Anaconda Prompt`. Inside there, the conda commands
work out-of-the-box: checking out different environments, installing things, etc..


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