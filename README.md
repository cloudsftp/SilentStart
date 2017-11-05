# Silent Start for MacBook

## Mechanism

In this directory there are 2 scripts. One to mute the computer completely and one to unmute it.

#### Muting

```bash
#!/bin/bash
osascript -e 'set volume with output muted'
```

#### Unmuting

```bash
#!/bin/bash
osascript -e 'set volume without output muted'
```

The mechanism we use to mute the very sound at startup is fairly simple.
We use default hooks by apple to mute the computer, when you log off and unmute it, when you log in.

What you have to do in order to install the scripts properly, will be specified in the following paragraphs.

## Installation

#### Scripts

The scripts can be anywhere on your Mac. Just be sure not to delete them.

When they are placed somewhere save, you need to make them executable. This can be done by the following command:

```bash
sudo chmod u+x /path/to/script.sh
```

Run this command for both scripts and proceed.

#### Hooks

Now you can hook the scripts to the default hooks of OSX.

First you need to make sure, that the hooks are not used.

```bash
sudo defaults read com.apple.loginwindow LoginHook
sudo defaults read com.apple.loginwindow LogoutHook
```

If they are not used, you can hook your scripts.

First hook the mute script to the LogoutHook.

```bash
sudo defaults write com.apple.loginwindow LogoutHook /path/to/mute-script.sh
```

Then hook the unmute script to the LoginHook.

```bash
sudo defaults write com.apple.loginwindow LoginHook /path/to/unmute-script.sh
```

#### DONE
