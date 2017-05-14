---
layout: post
title: 使用 IDEA 来进行 Git merger 和 diff
description: "IDEA 的 diff 工具不错，我们可以用它来进行 Git merge 和 diff."
date:   2017-02-13 17:26:03
tags: ["Git", "IntelliJ IDEA"]
categories: ["Tools"]
comments: true
---

首先，把 IDEA 加入到你的环境变量 `PATH` 下，使之可以从命令行调用。

以 OS X 为例（UNIX 类似）：

``` shell
# 根据使用的 shell 环境的不同，把下面的指令加入 ~/.bashrc 或者 ~/.zshrc 中
export PATH="/Applications/IntelliJ\ IDEA\ CE.app/Contents/MacOS:$PATH"

# 使之生效
source ~/.bashrc
# 或
source ~/.zshrc
```

或者打开 IDEA，从菜单 Tools \| Create Command-line Launcher 为 IDEA 创建启动脚本，同样要确保创建的脚本在你的环境变量 `PATH` 下。



接下来配置 Git，把 IDEA 做为它的 merge 和 diff 工具。把下面的配置加入到 `~/.gitconfig` 文件中：

```
[merge]
    tool = intellij
[mergetool "intellij"]
    cmd = idea merge $(cd $(dirname "$LOCAL") && pwd)/$(basename "$LOCAL") $(cd $(dirname "$REMOTE") && pwd)/$(basename "$REMOTE") $(cd $(dirname "$BASE") && pwd)/$(basename "$BASE") $(cd $(dirname "$MERGED") && pwd)/$(basename "$MERGED")
    trustExitCode = true
[diff]
    tool = intellij
[difftool "intellij"]
    cmd = idea diff $(cd $(dirname "$LOCAL") && pwd)/$(basename "$LOCAL") $(cd $(dirname "$REMOTE") && pwd)/$(basename "$REMOTE")
```

现在，在 Git CLI 下通过 `git mergetool`, `git difftool` 就可以使用 IDEA 来进行文件合并和差异对比了。