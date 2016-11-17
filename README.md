[![Gem Version](https://badge.fury.io/rb/tummy.svg)](https://rubygems.org/gems/tummy)
# Tummy

Use a Tmuxfile with your tmux configuration to easily manage sessions

![Demo](https://i.imgur.com/pBSixTt.gif)

## Installation

    $ gem install tummy

## Usage

put a `Tmuxfile` in your app's root by running the `tummy init` command

example Tmuxfile

```
session "z2-web"
directory "/home/minhajuddin/z2/web"

window "src", [
  pane("vim TODO"),
]

window "server-iex", [
  pane("iex -S mix phoenix.server"),
  # the last argument is passed to tmux as raw arguments
  pane("iex -S mix", :horizontal, "-l 20"),
  pane("git status", :vertical),
]

window "play", [
  pane("echo hey"),
  pane("date", :horizontal),
  pane("echo awesome", :vertical),
]

# if you comment this out it will focus the first window when the session is started
focus_window "server-iex"
# focus_window 0 # you can even focus a window by index starting at 0

```

Now whenever you run the `tummy` command from this directory it will setup your sessions properly
The `Tmuxfile` is a regular ruby file. If a tmux session with this name is already running it will just connect to that session
