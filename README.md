# Tools / Configuration
## Fix netflix, prime video when it's only playing sound, but no video
- turn "Use hardware acceleration when available" in Chrome settings off
- https://support.displaylink.com/forums/287786-displaylink-feature-suggestions/suggestions/44346744-netflix-playing-sound-only-no-picture

## reuse cmd to delete all local git branches
alias gbr="git branch | grep -v "master" | xargs git branch -D"

## install raycast and replace it with default spotlight search
https://manual.raycast.com/hotkey#22d51aad070942b5ba7cb35e5e15ee66

## Apps installieren
- brew
- brew install basictex

### change font
- Strg + Shift + P
- *Open User Settings (JSON)*
- tutotrial: https://codingshower.com/using-source-code-pro-font-in-vs-code-on-macos/
- Unter *"editor.fontSize"* *"editor.fontFamily": "SourceCodePro-Bold"* einfuegen.
- https://stackoverflow.com/questions/49731986/is-it-possible-to-change-the-default-font-of-vs-code-editor-to-source-code-pro-f

### setup verified commits
- follow this docs: https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key
       - note: enter correct no-reply github email
- run:
```
git config --global commit.gpgsign true
```
```
git config --global user.signingkey GPG_SIGNING_KEY
```
```
git config --global gpg.program /usr/local/bin/gpg
```

### Configure Sourcetree
- change project dir: in Preferences < General < Project folder to: `/Users/{username}/dev`

### Troubleshooting
![Screen Shot 2022-07-14 at 11 53 42 PM](https://user-images.githubusercontent.com/60318513/179097728-d343f70f-8aea-40eb-b225-00a084d7f348.png)

1. in vscode issue explained:
1. Your ascii colours are different between your installations of iTerm and VSC, so change those in your VSC or iTerm settings if you want the colours to be the same.
2. Your VSC doesn’t have a PowerLine-capable font installed. I recommend you switch your VSC terminal to the same font as your iTerm if you want it to just work.
fix:
- reinstall Source Code Pro font
- Go into VS Code’s Terminal settings, and somewhere in there, there should be a text field called “Terminal Font Family” or something. Change it to the same font family you use in iTerm.


## IntelliJ
### Plugins
- **Settings Sync**
- Docker
- GitHub Copilot
- Atom Material Icons
- Monokai Pro Theme
- Protocol Buffers

### Configuration
![Screen Shot 2022-07-15 at 12 53 03 PM](https://user-images.githubusercontent.com/60318513/179209725-55d808be-b58f-426d-83fa-cf21ba23677d.png)

![Screen Shot 2022-07-15 at 12 53 20 PM](https://user-images.githubusercontent.com/60318513/179209733-df282cef-cb28-4db6-bf75-c934c5c17977.png)



# Other tools
- database client: beekeeper studio
- useful link for auto formating: https://www.codementor.io/@myogeshchavan97/how-to-automatically-format-code-in-visual-studio-code-using-prettier-1nebhfbxak

# iterm

Download iterm: https://iterm2.com/downloads.html

## Tools
- brew
- jq (json prettier in cli); usage: `curl localhost:8080/todos | jq`

## oh-my-zsh
Download oh-my-zsh: https://ohmyz.sh/#install
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

## Dracula iterm theme
Download theme: https://draculatheme.com/iterm

## install fonts
- clone the repo: git clone https://github.com/powerline/fonts.git --depth=1
- cd fonts
- ./install.sh


## Configuration
### zsh
- import .zshrc from this repository

### theme
#### import Dracula theme to your profile
- iTerm2 > Preferences > Profiles > Colors
- Open the Color Presets > Select Import
- Select Dracula.itermcolors
- Select **Dracula** from Color Presets

#### select fonts
- iTerm2 > Preferences > Profiles > Text
- Select Font
- Search for "Source Code Pro for [...]"
======

#### activate nvim
- run `sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'`
https://github.com/junegunn/vim-plug#neovim
- Run `:PlugInstall` in any nvim envirionment while editing file


