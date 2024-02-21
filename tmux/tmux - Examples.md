https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/

TMUX’s authors describe it as a terminal multiplexer. Behind this fancy term hides a simple concept: Within one terminal window you can open multiple windows and split-views (called “panes” in tmux lingo).

1.  Start tmux:  
$ tmux

TMUX - uses C-b as prefix.
C -b equals hold Ctrl + b and release

2.  Split screen left / right:
C -b %

3.  Split screen top / bottom:
C -b "

4.  Navigate panes:
C -b <arrow key>

5.  Closing panes:
$ exit 		OR hit Ctrl+d

6. Create new Window:
C -b c 

7.  Switching Windows:
C -b p 		= previous
C -b n		= next
C -b <number>	= the numbered window

8.  Detaching a session - Keeps all sessions running in the background
C -b d		= detaches current session
C -b D		= gives you a choice of which session

9.  Listing TMUX sessions:
$ tmux ls

10.  Attach to TMUX session:
$ tmux attach -t 0

11. TMUX create a new session and give sessions names with a database:
$ tmux new -s database

12.  Rename an existing session:
$ tmux rename-session -t 0 database 

13.  Then the next time you attach to a session just use this from there on out:
$ tmux attach -t database