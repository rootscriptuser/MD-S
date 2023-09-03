# You can use xmodmap in terminal to swap Caps Lock with Esc:
```
xmodmap -e "keycode 9 = Caps_Lock NoSymbol Caps_Lock"   #this will make Esc to act as Caps Lock
xmodmap -e "keycode 66 = Escape NoSymbol Escape"        #this will make Caps Lock to act as Esc
```
> To get this change for every session, after you have run the ​​previous commands create a file called .xmodmap with the new keymaps, using the following command:

`xmodmap -pke > ~/.xmodmap `

> Then, create a file called .xinitrc in your home directory, containing the following line/command:

` xmodmap .xmodmap `

