# shell 帮助文档
官方文档地址：https://google.github.io/styleguide/shellguide.html

## 目录
* [Background](#Background)
  * [使用什么 shell](#使用什么 shell)
* [shell 文件和解释器](#shell 文件和解释器)
  * [文件扩展名](#文件扩展名)
  * [SUID/SGID](#SUID/SGID)
* [Environment](#Environment)
  * [STDOUT vs STDERR](#STDOUT vs STDERR)
        
## Background
### 使用什么 shell
Bash 是唯一允许用于可执行程序的 shell 脚本语言。

可执行文件必须以 `#!/bin/bash` 开头且使用最小数作为标志。使用 set 来设置 shell 选项，这样调用脚本为 `bash script_name` 不会破坏它的功能。

限制所有的可执行 shell 脚本为 bash，这为我们提供了一致的 shell 语言，可以安装到我们的所有机器上。

唯一的例外是 shell 脚本依赖编码规范。如 Solaris SVR4 包，它需要所有的脚本使用 Bourne shell 

## shell 文件和解释器
### 文件扩展名
可执行文件不应该有扩展名（强烈建议）或 `.sh` 扩展名。库必须有 `.sh` 扩展名，并且是不可执行的。

在执行可执行文件时，不需要知道它是什么编程语言编写的，而且 shell 不需要使用扩展名，因此可执行文件最好不要使用扩展名

然而，对于库文件来说，知道它是什么语言是很重要的，有时需要使用不同语言类似的库。这允具有相同目的但不同语言的库文件具有相同的名称（除了特定于语言的后缀）。

### SUID/SGID
shell 脚本禁止使用 `SUID/SGID`

shell 脚本有太多的安全问题，使得它几乎不可能足够安全的使用 `SUID/SGID`。虽然 bash 确实难以运行 `SUID`，但在某些平台上仍然是可能的，这就是为什么我们明确禁止它。

如果需要的话，通过 `sudo` 来提供高级访问。

## Environment
### STDOUT vs STDERR
