Website:  https://askubuntu.com/questions/1386836/wsl2-vscodes-shell-command-code-no-longer-working-in-linux-terminal

Within the WSL terminal, type rm -r ~/.vscode-server to delete the VS Code WSL server.

Exit the terminal and from your PowerShell/Cmd, run wsl --shutdown . Then you can log in back to your WSL and run code . and it should work normally.

