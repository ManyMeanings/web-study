### 需求

拷贝当前目录下的文件夹及其内容至指定目录，并刷新装载驱动。

### 难点

- 在 electron 桌面应用开发中执行终端命令。
- 只申请一次权限。

### 思路

- 使用`npm`安装`sudo-prompt`执行需要 root 权限的命令。
- 使用`Node.js`的`path`获取当前程序的路径。
- 把命令写在脚本文件里，执行脚本文件。

### 代码

```js
//核心代码

var sudo = require("sudo-prompt");
var options = {
  name: "Electron",
};

const resolve = require("path");
const dir = process.cwd();

var btn = document.querySelector("#btn");

btn.addEventListener("click", (e) => {
  console.log("btn active");
  sudo.exec(`${dir}/mount.sh`, options, (error) => {
    if (error) throw error;
  });
});
```

```bash
#!/bin/bash
cp -r ./myDir /Library/Audio/Plug-Ins/HAL
launchctl kickstart -kp system/com.apple.audio.coreaudiod
```
