## 去掉“隔离标签（quarantine attribute）”，让系统不再认为它来自“危险来源”
- sudo xattr -rd com.apple.quarantine /Applications/xxxx.app
## 启用睡眠
- sudo pmset -a disablesleep 0