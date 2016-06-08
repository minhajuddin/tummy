# Tummy

Use a Tmuxfile with your tmux configuration to easily manage sessions

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
  pane("iex -S mix", :horizontal),
  pane("git status", :vertical),
]

window "play", [
  pane("echo hey"),
  pane("date", :horizontal),
  pane("echo awesome", :vertical),
]

```

Now whenever you run the `tummy` command from this directory it will setup your sessions properly
The `Tmuxfile` is a regular ruby file. If a tmux session with this name is already running it will just connect to that session
