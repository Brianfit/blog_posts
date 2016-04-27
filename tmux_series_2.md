**Author:** Jacobm001

**Publish Status:** draft

**Suggested Tags:** raspberrypi, raspbian, tmux

# Tmux 102: Getting to know Tmux.

[Tmux 101](https://raspberrypise.tumblr.com/post/141348857424/tmux-101-installing-from-source) discussed how to install Tmux from the source.  This week, we'll be focusing on Tmux's basic usage.

## Launching Tmux

### Open Tmux

Tmux is launched form a standard terminal. If you're in a desktop environment, you'll need to open a terminal, otherwise simply type the command `tmux`. At this point, you should see a terminal that looks similar to what you're accustomed to, with a yellow-green bar on the bottom with some writing on it. Congrats, you've started your first Tmux session!

Before we go any further, it's probably important to clarify the vocabulary that will be used in this post.

- **session:** An instance of Tmux. You can have multiple sessions running at the same time, but in most cases you will only ever interact with one of them at a time. Think of a session like an instance of a web browser.
- **window:** In Tmux, a window is similar to a web browser's tab.
- **pane:** The actual interactive shell provided by Tmux. By default, each window has one pane, but the window can be divided into multiple panes. This can be though of like different content areas within a browser tab.

### What do all the labels mean?

Tmux manages to fit a surprising amount of information into a relatively small space. On the far left, we see a number (probably `0`) in brackets. This indicates our session name. By default, the session name is `0`. If this session is detached, and another one is created, the new session name will be auto incremented to 1.

Next we see a list of the windows, and their names. Each window is given an auto incremented number, and by default its name is whatever application is currently running on the focused pane. The asterisk (`*`) indicates that window `0:bash` is active.

### Using Tmux

As you may have guessed, you can start entering commands. If you run the command `uptime`, you'll see an output much like you'd normally expect. Where Tmux gets interesting, is the pane and window functions mentioned earlier. To enter a command in Tmux you need to use the *bind key*. The default bind key is `ctrl-b`. Once pressed, the next key entered will register a given command. If you're familiar with Emacs, you'll find this familiar.

For a simple example, we'll run two applications simultaneously. For me, it's common to be writing a program, and want to test it at the same time. To demonstrate, create a new python script by typing `nano test.py`. You should now have a basic text editor that takes the entire screen. Go ahead and put the lines:

    print("Hello, World!")
    print("I'm playing with Tmux.")

Now, save the file by pressing `ctrl-o`, but don't close it! Instead, we're going to open a new pane. This is done by pressing `ctrl-b` **then** `%`. Notice that these are two separate actions. Press the first set of keys, then the second.

You should now see an entirely new pane, and your cursor should have been moved to it automatically. Run your script with the command `python3 test.py`, and you'll see the output as expected, right alongside your file editor. You can get back to the editor by `ctrl-b` and then the left keyboard arrow.

That's it! You now know the basics of using Tmux. 

### Some other commands to know:

- split a pane horizontally: `ctrl-b` then `"`
- close a pane: `ctrl-b` then `x`
- create a window: `ctrl-b` then `c`
- change to the next window: `ctrl-b` then `n`
- change to the previous window: `ctrl-b` then `p`
- change to a specific window: `ctrl-b` then its corresponding number
- to close a window, simply close every pane in the window.

### What's next?

In the next article I'll go over how to use Tmux to keep programs running after disconnect, and basic scripting solutions with Tmux.
