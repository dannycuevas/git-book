
https://git-scm.com/book/en/v2/Appendix-C:-Git-Commands-Setup-and-Config
### git config core.editor commands


Accompanying the configuration instructions in [Your Editor](https://git-scm.com/book/en/v2/ch00/_editor), many editors can be set as follows:

| Editor                                                        | Configuration command                                                                                                                          |
| ------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Atom                                                          | `git config --global core.editor "atom --wait"`                                                                                                |
| BBEdit (macOS, with command line tools)                       | `git config --global core.editor "bbedit -w"`                                                                                                  |
| Emacs                                                         | `git config --global core.editor emacs`                                                                                                        |
| Gedit (Linux)                                                 | `git config --global core.editor "gedit --wait --new-window"`                                                                                  |
| Gvim (Windows 64-bit)                                         | `git config --global core.editor "'C:\Program Files\Vim\vim72\gvim.exe' --nofork '%*'"` (Also see note below)                                  |
| Helix                                                         | `git config --global core.editor "hx"`                                                                                                         |
| Kate (Linux)                                                  | `git config --global core.editor "kate --block"`                                                                                               |
| nano                                                          | `git config --global core.editor "nano -w"`                                                                                                    |
| Notepad (Windows 64-bit)                                      | `git config core.editor notepad`                                                                                                               |
| Notepad++ (Windows 64-bit)                                    | `git config --global core.editor "'C:\Program Files\Notepad++\notepad++.exe' -multiInst -notabbar -nosession -noPlugin"` (Also see note below) |
| Scratch (Linux)                                               | `git config --global core.editor "scratch-text-editor"`                                                                                        |
| Sublime Text (macOS)                                          | `git config --global core.editor "/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl --new-window --wait"`                        |
| Sublime Text (Windows 64-bit)                                 | `git config --global core.editor "'C:\Program Files\Sublime Text 3\sublime_text.exe' -w"` (Also see note below)                                |
| TextEdit (macOS)                                              | `git config --global core.editor "open --wait-apps --new -e"`                                                                                  |
| Textmate                                                      | `git config --global core.editor "mate -w"`                                                                                                    |
| Textpad (Windows 64-bit)                                      | `git config --global core.editor "'C:\Program Files\TextPad 5\TextPad.exe' -m"` (Also see note below)                                          |
| UltraEdit (Windows 64-bit)                                    | `git config --global core.editor Uedit32`                                                                                                      |
| Vim                                                           | `git config --global core.editor "vim --nofork"`                                                                                               |
| Visual Studio Code                                            | `git config --global core.editor "code --wait"`                                                                                                |
| VSCodium (Free/Libre Open Source Software Binaries of VSCode) | `git config --global core.editor "codium --wait"`                                                                                              |
| WordPad                                                       | `git config --global core.editor "'C:\Program Files\Windows NT\Accessories\wordpad.exe'"`                                                      |
| Xi                                                            | `git config --global core.editor "xi --wait"`                                                                                                  |

|   |   |
|---|---|
|Note|If you have a 32-bit editor on a Windows 64-bit system, the program will be installed in `C:\Program Files (x86)\` rather than `C:\Program Files\` as in the table above.|

### git help

The `git help` command is used to show you all the documentation shipped with Git about any command. While we’re giving a rough overview of most of the more popular ones in this appendix, for a full listing of all of the possible options and flags for every command, you can always run `git help <command>`.
