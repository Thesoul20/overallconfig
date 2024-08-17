# how to use

需要在yml 文件中写入当前键盘的配置，目前已经写出的配置有`aigo87` 无线键盘与`logic610`有线键盘。主要的改动就是把`Caplock` 换成`Ctrl`，还有一些针对于光标移动的设置。

在配置完成设置之后，将目标的配置文件地址写入到文件`main_usage_remap.sh`中，用以在Linux 自动启动该服务。

## 仅改变键位
像是把`Caplock` 换成`Ctrl`，需要在`modmap`部分写入这样的配置：
```yaml
modmap:
  - name: all
    remap:
      CAPSLOCK: LEFTCTRL
```

## 新建快捷键

可以自己设置快捷键，对应的需要写入在`keymap`部分：

```yaml
keymap:
  - name: all
    remap:
      C-l: right
      C-n: left
      C-k: up
      C-j: down
      C-e: Key_end
      C-i: Key_home
      C-enter: [Key_end, Key_enter]

  - application:
      only: [okular]
    name: pdf_reader
    remap:
      KEY_J: down
      KEY_K: up
      KEY_SPACE: [KEY_SPACE, up, up, up]
``` 
更多的设置可以查看Github 的repo：https://github.com/xremap/xremap?tab=readme-ov-file

你可以在这里找到所有有关于键位的名称：https://github.com/emberian/evdev/blob/1d020f11b283b0648427a2844b6b980f1a268221/src/scancodes.rs#L26-L572

# 其它设置
xremap 需要使用特殊的权限才可以正常的启动，这个时候需要设置一个特别的用户组。

之后就需要将文件`xremap.service` 文件添加到Linux 自动启动服务。

# end
