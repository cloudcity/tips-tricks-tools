# Tips, tricks, and tools

A little repo with some handy productivity saving configuration and tools that we like.

## Mac apps
- [Rectangle](https://rectangleapp.com/) - Move and resize windows in macOS using keyboard shortcuts or snap areas. Makes putting windows side by side on your screen so easy! The recommended settings are great.

## Editors
- [VSCode](https://code.visualstudio.com/) — A lot of the tools in this repo are for those using VSCode. If you're not, that's cool! All IDEs are welcome 🤗

Install the [shell command for VSCode](https://code.visualstudio.com/docs/setup/mac) so that you can use `code` in your shell to open a directory.

## Extensions


### Git
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens]): Supercharge Git within VS Code — Visualize code authorship at a glance via Git blame annotations and CodeLens, seamlessly navigate and explore Git repositories, gain valuable insights via rich visualizations and powerful comparison commands, and so much more
  
### Pairing
- [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare): Real-time collaborative development from the comfort of your favorite tools.

### Testing
- [Go to Spec](https://marketplace.visualstudio.com/items?itemName=Lourenci.go-to-spec): Switch between the code and the spec file
- [Switch to test](https://marketplace.visualstudio.com/items?itemName=eskimoblood.create-test): This extension will open the coresponding test file for the opened source file. If the file does not exist, it will create a new one.
  
### Linting/Formatting
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint): Integrates ESLint into VS Code.
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode): Code formatter using prettier
- [ruby-rubocop](https://marketplace.visualstudio.com/items?itemName=misogi.ruby-rubocop): execute rubocop for current Ruby code.
- [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag): Automatically rename paired HTML/XML tag, same as Visual Studio IDE does.

### General
- [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync): Synchronize Settings, Snippets, Themes, File Icons, Launch, Keybindings, Workspaces and Extensions Across Multiple Machines Using GitHub Gist.
- [change-case](https://marketplace.visualstudio.com/items?itemName=wmaurer.change-case): Quickly change the case (camelCase, CONSTANT_CASE, snake_case, etc) of the current selection or current word
- [Peacock](https://marketplace.visualstudio.com/items?itemName=johnpapa.vscode-peacock): Subtly change the color of your Visual Studio Code workspace. Ideal when you have multiple VS Code instances, use VS Live Share, or use VS Code's Remote features, and you want to quickly identify your editor.
- [:emojisense:](https://marketplace.visualstudio.com/items?itemName=bierner.emojisense): Adds suggestions and autocomplete for emoji

### Settings
Please see [settings.json](settings.json) for info on how to configure these extensions for productivity.

- Auto save files when you blur or navigate away from them
- Custom colors for matching brackets, parentheses, etc (choose your own colors!)
- Lint and autoformat files on save 

## Snippets
[Code snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets) are templates that make it easier to enter repeating code patterns, such as loops or conditional-statements.

To add new snippets, go to Code > Preferences > User snippets and then choose the language and file type you want this snippet available in.

Below you'll find our favorite code snippets

- [Ruby](ruby-snippets.json) snippets
- [Vanilla JS](js-snippets.json) snippets
- [React](react-snippets.json) snippets
- [Vue](vue-snippets.json) snippets


## Aliases

Delete merged branches that are not master or main
```bash
alias gclean="git branch --merged | egrep -v '(^\*|master|main)' | xargs git branch -d"
```

Delete branches squash merged into main to keep `git branch` clean (name the alias whatever you want)
```bash
alias gsqclean='git checkout -q main && git for-each-ref refs/heads/ "--format=%(refname:short)" | while read branch; do mergeBase=$(git merge-base main $branch) && [[ $(git cherry main $(git commit-tree $(git rev-parse $branch^{tree}) -p $mergeBase -m _)) == "-"* ]] && git branch -D $branch; done'
```

## Other

- [.pryrc](.pryrc) to get aliases while debugging with `pry`, e.g. `c` instead of `continue`, etc.