# Issues

### Solution to known issues

#### Error: ENOSPC: System limit for number of file watchers reached

(https://github.com/nuxt/nuxt.js/issues/6172)
```
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```
VS Code on Linux

(https://code.visualstudio.com/docs/setup/linux#_visual-studio-code-is-unable-to-watch-for-file-changes-in-this-large-workspace-error-enospc)



