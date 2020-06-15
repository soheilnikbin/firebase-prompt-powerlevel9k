# Add a project alias to firebase project

When you select a Firebase project during project initialization, the project is automatically assigned the alias of default. However, to allow project-specific commands to run against a different Firebase project but still use the same project directory, run the following command from within your project directory: 
```
firebase use --add
```
And by running ```firebase use [project_id]``` you can toggle between different environment(projects).

source: https://firebase.google.com/docs/cli#add_alias

Well this is supper handy to switch between different environments but also supper easy to deploy development code into production env ;), Let's set up shell prompt to display us the current env on the famous Powerlevel10k theme.

Here is the link for how to install Powerlevel10k theme:
https://gist.github.com/kevin-smets/8568070

# Setup shell prompt for .p10k.zsh
Open Iterm2 and run ```vim ~/.p10k.zsh```, hit ```I``` on keyboard to edit shell.
Search for ```instant_prompt_example``` and past below code under it.
```
 function prompt_firebase() {
    local fb_project=$(grep \"$(pwd)\" ~/.config/configstore/firebase-tools.json | cut -d" " -f2)
    if [[ -n $fb_project ]]; then
    p10k segment -t $fb_project
    fi
  }

  typeset -g POWERLEVEL9K_FIREBASE_FOREGROUND='009'
  typeset -g POWERLEVEL9K_FIREBASE_BACKGROUND='232'
  typeset -g POWERLEVEL9K_FIREBASE_VISUAL_IDENTIFIER_EXPANSION='🔥'
``` 
Now scroll all the way up to find ```POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS``` and past ```firebase``` at the and. Feel free to paste it under ```Line #1``` or ```Line #2```, I recommend Line 2.

 - Now hit ```esc```
 - Hold Shift + ```:```
 - Type ```wq```
 - And hit Enter
 
 That's it, now you can navigate to project directory and see your project env all the time.
![Demo](/assets/final.png)
