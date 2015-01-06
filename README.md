*Author:* Feng Shu <tumashu@gmail.com>, Fabrice Niessen<br>
*Version:* 0.01<br>

# Stumpwm Tips #

## 在登陆管理器中显示stumpwm选项 ##
编辑 /usr/share/xsessions/stumpwm.desktop 文件：

```
[Desktop Entry]
Encoding=UTF-8
Name=stumpwm
Comment=This session logs you into StumpWM (a minimalistic window manager)
Exec=/path/to/stumpwm
Type=Application
```

## 设置默认桌面管理器为stumpwm ##
1. 如果使用gdm,lightdm等，添加下面代码到文件 ~/.xsession，
2. 如果使用startx命令登陆桌面，则添加下面代码到文件 ~/.xinitrc

```shell
# lxpanel &
# bmpanel2 &
if [ -f ~/.bashrc ]; then
source ~/.bashrc
fi
exec /your/path/stumpwm
```
## 设置中文字体 ##
建议使用 xfont-unifont，这个字体是等宽字体，虽然中英文不能完全对齐，
但显示效果很好，类似winxp。

另外，也可以通过 "ttf-fonts" 模块来使用ttf字体，但到目前为止<2015-01-06>，
这个字体模块还存在性能问题，暂时不建议中文用户使用。

## 安装辅助taskbar ##
StumpWM 自带 mode-line 功能，配置灵活，但缺点是不能使用鼠标切换窗口。

我们可以在StumpWM加载之前启动一个附属任务栏程序，比如：lxpanel
并将其设置为自动隐藏（防止遮挡窗口）。

辅助任务栏和 mode-line 配合使用，非常方便。

## 其他推荐程序 ##

1. xfce4-power-manager(xfce电源管理软件)
2. xscreensaver(屏幕保护程序)
3. volti(一个小巧的音量调节器)
4. xdotool(linux下面的按键精灵，我用这个软件自动拷贝文本)
5. xsel(命令行程序，用来管理剪切板的内容)

## 设置debian menu ##
1. 将 ./bin/menu-method/stumpwm 文件复制到 /etc/menu-method/ 目录。
2. 按照需要编辑文件： /etc/menu-method/stumpwn （必需步骤）。
3. 运行命令：sudo update-menus
4. 在StumpWM配置中添加类似下面的一行配置，注意：按照个人实际情况更改路径。

```lisp
(setf *debian-menu-file* "/usr/share/common-lisp/source/stumpwm/contrib/stumpwm.menu")
```
## 美化Java程序的字体 ##
在/etc/environment文件中添加一行：

```shell
_JAVA_OPTIONS="-Dawt.useSystemAAFontSettings=on -Dswing.aatext=true"
```


---
Converted from `stumpwmrc` by [*el2markdown*](https://github.com/Lindydancer/el2markdown).
