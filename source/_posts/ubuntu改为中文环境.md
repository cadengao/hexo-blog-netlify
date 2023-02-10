---
title: ubuntu改为中文环境
date: 2023-02-10 12:22:50
updated: 2023-02-10 12:22:50
comments: true
---
# 修改步骤

1. 检查当前环境，执行

```bash
echo $LANG
```

> **注**：如果屏幕显示`en_US.UTF-8`，说明是英语环境(有中文字符文件时会乱码)，需要切换到中文环境，中文环境下会显示`zh_CN.UTF-8`。

2. 安装中文语言包：执行

```bash
apt-get update && apt-get install language-pack-zh-hansvim /etc/default/locale
```

3. 更改locale：执行

```bash
LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN:zh"
LC_NUMERIC="zh_CN"
LC_TIME="zh_CN"
LC_MONETARY="zh_CN"
LC_PAPER="zh_CN"
LC_NAME="zh_CN"
LC_ADDRESS="zh_CN"
LC_TELEPHONE="zh_CN"
LC_MEASUREMENT="zh_CN"
LC_IDENTIFICATION="zh_CN"
LC_ALL="zh_CN.UTF-8"
```

,用以下内容直接**覆盖**

```
LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN:zh"
LC_NUMERIC="zh_CN"
LC_TIME="zh_CN"
LC_MONETARY="zh_CN"
LC_PAPER="zh_CN"
LC_NAME="zh_CN"
LC_ADDRESS="zh_CN"
LC_TELEPHONE="zh_CN"
LC_MEASUREMENT="zh_CN"
LC_IDENTIFICATION="zh_CN"
LC_ALL="zh_CN.UTF-8"
```

4. 更改environment：执行

```bash
vim /etc/environment
```

,用以下内容**覆盖**(注：原来可能有首行“PATH=...”,如果有的话，不要动，另起一行**追加**即可)

```
LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN:zh"
LC_NUMERIC="zh_CN"
LC_TIME="zh_CN"
LC_MONETARY="zh_CN"
LC_PAPER="zh_CN"
LC_NAME="zh_CN"
LC_ADDRESS="zh_CN"
LC_TELEPHONE="zh_CN"
LC_MEASUREMENT="zh_CN"
LC_IDENTIFICATION="zh_CN"
LC_ALL="zh_CN.UTF-8"
```

5. 重启：执行

```bash
reboot
```

# 其他问题

有些机器会不生效，重启后会报“bash: warning: setlocale: LC_ALL: cannot change locale (zh_CN.UTF-8)”错误，需要执行

```bash
echo "export LC_ALL=zh_CN.UTF-8" >> /etc/profile
source /etc/profile
```