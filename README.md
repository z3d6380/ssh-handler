# ssh-handler
If you are using some simple web applications that provides list of devices that you can connect using ssh it is useful to auto launch terminal with ssh connection started

## Inspired by this post:
https://soultrace.net/open-ssh-urls-in-chrome-and-firefox/

## Installation:

1. First, place `ssh-handler.sh` in `~/bin` (you may need to `chmod u+x` the file)

2. Next, place the `.zshssh` file in your home directory where your `.bashrc` or `.zshrc` files are (you may have to `chmod u+x ./zshssh` to make file executable)

3. You will also need to add the following lines into either your `.bashrc` or `.zshrc` file:
   ```bash
   eval "$(ssh-agent -s)" > /dev/null 2>&1
   ssh-add /home/user/your-private-key > /dev/null 2>&1
   # ssh-add /home/user/add-any-other-private-keys-below > /dev/null 2>&1
   trap 'test -n "$SSH_AGENT_PID" && eval $(/usr/bin/ssh-agent -k)' 0
   ```

4. Place the `ssh-handler.desktop` file in `~/.local/share/applications` (you may need to edit the `Exec` path in the `.desktop` file to match where your `ssh-handler.sh` file is located)

5. Finally, add `x-scheme-handler/ssh=ssh-handler.desktop` as an entry under the `[Default Applications]` section in the `mimeapps.list` file that is in the `~/.local/share/applications` directory

## Working Install

![image](https://github.com/z3d6380/ssh-handler/assets/73666574/49560bb6-3bf2-4786-8af6-15cd0af3190b)

![image](https://github.com/z3d6380/ssh-handler/assets/73666574/5d5b701b-ea27-4c91-9223-5c6c7d8f2878)
