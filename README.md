# GIGA-beest
## Turn GNU nano editor into a fancy &amp; powerful editor

GNU nano is a lovely little editor that comes preinstalled in many GNU/Linux distributions. It is a very handy and capable editor despite its small footprint. According to documentation available on GNU nano's website,  
> GNU nano was designed to be a free replacement for the Pico text editor, part of the Pine email suite from The University of Washington. It aimed to "emulate Pico as closely as is reasonable and then include extra functionality".  

Perhaps this aim of emulating Pico is responsible for less than friendly default keybindings of nano. And for some unknown and obscure reasons many of nano's cool features are disabled by default. This results in nano coming out across as a plain Jane little text editor that is uncool. And that is not true.  

It is so darn easy to unleash the true potential of nano and make it shine. All one needs to do is create a file with the name <code>.nanorc</code> in the <code>$HOME</code> directory,  
```text
touch $HOME/.nanorc
```
Next open that file and simply paste the following content in it,  
```text
set atblanks
set autoindent
set backup
set backupdir "/home/$USER/Documents/Nano_Backups/"
set boldtext
set constantshow
set cutfromcursor
set indicator
set linenumbers
set magic
set minibar
set mouse
set showcursor
set softwrap
set speller "aspell -x -c"
set trimblanks
set whitespace "»·"
set zap
set multibuffer

set titlecolor bold,lightwhite,blue
set promptcolor lightwhite,lightblack
set statuscolor bold,lightwhite,green
set errorcolor bold,lightwhite,red
set spotlightcolor black,lime
set selectedcolor lightwhite,magenta
set stripecolor ,yellow
set scrollercolor cyan
set numbercolor cyan
set keycolor cyan
set functioncolor green

include "/usr/share/nano/*.nanorc"

bind ^Q exit all
bind ^S savefile main
bind ^W writeout main
bind ^O insert main
bind ^H help all
bind ^H exit help
bind ^F whereis all
bind ^G findnext all
bind ^B wherewas all
bind ^D findprevious all
bind ^R replace main
bind ^X cut main
bind ^C copy main
bind ^V paste all
bind ^P location main
bind ^E execute main
bind ^A mark main
unbind ^K main
unbind ^U all
unbind ^N main
unbind ^Y all
unbind M-J main
unbind M-T main
bind ^T gotoline main
bind ^T gotodir browser
bind ^T cutrestoffile execute
bind ^L linter execute
bind M-U undo main
bind M-R redo main
bind ^Z undo main
bind ^Y redo main

```
You'll have to replace <code>$USER</code> in the following line,  
<code>set backupdir "/home/$USER/Documents/Nano_Backups/"</code>  
with your actual <code>username</code> and then save this file.  

Wouldn't it be nice if the colors in nano were different for a normal user and a root user? Yes, for sure. To do so create an empty <code>.nanorc</code> file in the root's directory. You'll have to do this with the help of either <code>sudo</code> or <code>su</code>,  
```text
touch /root/.nanorc
```
Open that file and paste this content in it,  
```text
set atblanks
set autoindent
set backup
set backupdir "/root/Documents/Nano_Backups/"
set boldtext
set constantshow
set cutfromcursor
set indicator
set linenumbers
set magic
set minibar
set mouse
set showcursor
set softwrap
set speller "aspell -x -c"
set trimblanks
set whitespace "»·"
set zap
set multibuffer

set titlecolor bold,lightwhite,magenta
set promptcolor black,yellow
set statuscolor bold,lightwhite,magenta
set errorcolor bold,lightwhite,red
set spotlightcolor black,orange
set selectedcolor lightwhite,cyan
set stripecolor ,yellow
set scrollercolor magenta
set numbercolor magenta
set keycolor lightmagenta
set functioncolor magenta

include "/usr/share/nano/*.nanorc"

bind ^Q exit all
bind ^S savefile main
bind ^W writeout main
bind ^O insert main
bind ^H help all
bind ^H exit help
bind ^F whereis all
bind ^G findnext all
bind ^B wherewas all
bind ^D findprevious all
bind ^R replace main
bind ^X cut main
bind ^C copy main
bind ^V paste all
bind ^P location main
bind ^E execute main
bind ^A mark main
unbind ^K main
unbind ^U all
unbind ^N main
unbind ^Y all
unbind M-J main
unbind M-T main
bind ^T gotoline main
bind ^T gotodir browser
bind ^T cutrestoffile execute
bind ^L linter execute
bind M-U undo main
bind M-R redo main
bind ^Z undo main
bind ^Y redo main

```

Finally we need to create a couple of directories to save the backup files. Backups are enabled in nano and this is a good choice if you ask me.  
Backup directory for a normal user,  
```text
mkdir -p $HOME/Documents/Nano_Backups/
```
And backup directory for root user. Do run this command as <code>sudo</code> or <code>su</code>,  
```text
mkdir -p /root/Documents/Nano_Backups/
```

Spell checker is enabled in nano via this configuration but to utilize it you'll have to install <code>aspell</code> and <code>aspell-dictionary</code> from your package manager.  

Kudos! We have turned a timid GNU nano into a powerful wildebeest.  
And don't forget what some wise man famously and rightly said,  
> Good Things Come in Small Packages.

Bye Bye.
