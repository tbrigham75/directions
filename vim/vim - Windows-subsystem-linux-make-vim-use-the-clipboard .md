https://superuser.com/questions/1291425/windows-subsystem-linux-make-vim-use-the-clipboard

MAY 2023 SOLUTION

The following worked for me (2023/05/15, WSL Ubuntu 20.04.5 LTS):

    Ensure your WSL has X11 support: https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps

    Ensure vim is installed with clipboard support. Running vim --version | grep clipboard should say +clipboard, not -clipboard.

If you don't have clipboard support, install a vim package compiled with clipboard support:

sudo apt-get install vim-gtk

(This is similar to Aerows answer but you don't need VcXsrv)
