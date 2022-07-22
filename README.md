# Tools / Configuration
## Apps installieren
- brew
- Vysor
- Xcode
- Visual Studio Code
- DevCleaner
- IntelliJ
- iterm
- Discord
- Slack
- Spotify
- Docker
- Postman
- Adblock (Safari Extension)
- JSONPeep (Safari Extension)
- Chrome
- git
- Vysor
- Zoom
- Google Drive
- Google Calendar
- Uninstaller sensei
- Notion
- Anki
- GoodNotes
- Magnet
- BetterTouchTool
- MacMouseFix (fuer zoomen auf Internetseiten etc)
- Camo (fuer Ipad in meetings als webcam.)

- SelfControl
- toggl (TimeTracking)
- Password manager
- Grammarly
- MindNode
- Antivierenprogramm: bitdefender
- (Bear)

## Visual Studio Code
### Plugins
- Code Runner
- Color Picker
- Dart
- Docker
- Flutter
- Flutter Tree
- Go
- gopls
- Kubernetes
- Monokai Pro
- Icons
- Remote - Containers
- Test Adapter Converter
- Test Explorer UI
- YAML
- Tabnine
- GitHub Copilot
- Error Lens
- Thunder Client
- SQLite Viewer
- vscode-proto3
- gotemplate-syntax
- Makefile Tools

### change font
- Strg + Shift + P
- *Open Settings (JSON)*
- tutotrial: https://codingshower.com/using-source-code-pro-font-in-vs-code-on-macos/
- Unter *"editor.fontSize"* *"editor.fontFamily": "Source Code Pro"* einfuegen.
- https://stackoverflow.com/questions/49731986/is-it-possible-to-change-the-default-font-of-vs-code-editor-to-source-code-pro-f

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


