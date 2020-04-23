# Shadowplay On Linux

Shadowplay's replay feature on Linux

- compatible with nvenc, vaapi, and qsv

## Prerequisites

- Have FFMPEG installed
	- `sudo pacman -S ffmpeg`
- Have Xbindkeys installed
	- `sudo pacman -S xbindkeys`

## Configuration

- Use `-f` or `--framerate` to set your desired recording framerate. Default is 30.

- Use `-m` or `--monitor-number` to chose the monitor to record

- Use `-b` or `--buffer` to chose your desired save time. Default is 00:05:00 for 5min.

- Change `VIDEO_FOLDER` to the folder where you want replays to be saved. Default is your XDG Videos directory or as fallback `$HOME/Videos/`

## Setup

### Keybind Setup
First, configure the key (or key combo) you want to use in order to save your replays.
- For instructions on how to bind keys, check [here](http://xahlee.info/linux/linux_xbindkeys_tutorial.html) 
- Consider making another bind for killing ShadowPlay. (See below)
- Bind a key to the command `killall --user $USER --ignore-case --signal SIGTERM  ffmpeg` so it looks something like this:
```
# make F9 save Shadowplay replay
"killall --user $USER --ignore-case --signal SIGTERM ffmpeg"
   F9

# make F10 kill Shadowplay
"killall -s1 ffmpeg"
   F10
```
- Start xbindkeys with `xbindkeys -f ~/.xbindkeysrc`, or reload it with `killall -s1 xbindkeys` if it's already running, for the new bind to take effect.

### Script

- Run the Shadowplay script with `./shadowplay` in a terminal
- Press your configured hotkey to save the replay. 

## TODO
- Systemd service/timer integration
- Automatic deletion of video recorded older than the replay buffer
- Add support for recording system sound

## Notes
When recording for long intervals, it may take some time to save your replays.

Heavily inspired by [Toqozz's script](https://github.com/Toqozz/shadowplay-linux).

Thank you [Tyler](https://github.com/durcor) for answering my stupid questions while making this.
