# 常用命令

## 状态

 magit-status == git status

TAB键：如果你想查看修改了哪些内容，按下 Tab 键，Magit 会显示修改了哪些内容。这跟运行命令 git diff 文件名字 类似

s键：stage file

u:  unstage file

对应的命令行: git add -u <file>和 git reset HEAD <file>

### 提交更改

在同一个 Magit 窗口中，按下 c 键会显示一个提交窗口，其中提供了许多标志，比如 --all 用来暂存所有文件或者 --signoff 来往提交信息中添加签名行。

将光标移动到想要启用签名标志的行，然后按下回车。--signoff 文本会变成高亮，这说明该标志已经被启用。

再次按下 c 键会显示一个窗口供你输入提交信息。

最后，使用 C-c C-c(按键 Ctrl+cc 的缩写形式) 来提交更改。

### 推送更改

更改提交后，提交行将会显示在 Recent commits 区域中显示。
将光标放到该提交处然后按下 p 来推送该变更。
