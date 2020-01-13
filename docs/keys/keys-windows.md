?> ![](https://notes.abelsu7.top/_media/windows.svg ':no-zoom')Windows

!> [![](https://notes.abelsu7.top/_media/windows.svg)Windows 中的键盘快捷方式 | Microsoft Support](https://support.microsoft.com/zh-cn/help/12445/windows-keyboard-shortcuts)

## Windows 快捷键

| Keys | Function |
| :-- | :-- |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+A** | 打开操作中心 |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+B** | 聚焦通知栏 |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+D** | 显示桌面 |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+Alt+D** | 显示日期和时间 |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+Shift+S** | 截屏 |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+Ctrl+方向** | 切换桌面 |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+PgUp/PgDn** | 前/后切换浏览器标签页 |
| <img src='https://notes.abelsu7.top/keys/logo/win10.svg' data-no-zoom></img>**+;** | 表情符号 |
| **Ctrl+Shift+B** | 打开表情及符号面版 |
| **Ctrl+Shift+F** | 输入法切换简/繁体 |
| **Shift+滚轮** | 水平方向滚动 |
| **F2** | 重命名 |
| **Shifit+F10** | 打开右键菜单 |

## CMD 命令

```bash
tasklist
regedit
taskschd.msc
gpedit.msc

# 启动/停止服务
net start mysql80
net stop mysql80

tasklist | findstr "<pattern string>"
```

## 推荐软件

- [![](logo/tweaker.png ':size=16')7+ Taskbar Tweaker | 解除状态栏靠左时最小宽度的限制![](logo/star.svg)](https://rammichael.com/7-taskbar-tweaker)

## 后台优化

- 关闭 Visual Studio 自动下载更新，否则后台 CPU 狂跑
- 关闭磁盘碎片整理计划，参见 [知乎](https://zhuanlan.zhihu.com/p/26142096)

## hosts 文件

```powershell
C:\Windows\System32\drivers\etc\hosts
```

## Windows Defender

- [Process Explorer - Microsoft](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer)
- [![](logo/csdn.ico ':size=16')解决 Antimalware Service Executable CPU，内存占用高的问题 | CSDN](https://blog.csdn.net/m0_37230651/article/details/80893639)
- [Surface 中 Antimalware Service Executable CPU 占用高，如何解决？| 知乎](https://www.zhihu.com/question/36613062)
- [win10 全盘扫描后Antimalware Service Executable CPU占用率过高 | Microsoft Community](https://answers.microsoft.com/zh-hans/protect/forum/all/win10/2eeba1c2-8292-49d4-ab06-e8bb4a712532)
- [Fixed: 'Antimalware Service Executable' High CPU on Windows 10 | driver easy](https://www.drivereasy.com/knowledge/antimalware-service-executable-high-disk-usage-windows-10-8-7-solved/)
- [How to fix 'Antimalware Service Executable' high CPU usage | EmsiSoft Blog](https://blog.emsisoft.com/en/28620/antimalware-service-executable/)

```bash
Windows Defender 
-> 病毒和威胁保护 
-> 管理设置 
-> 排除项
```

## Office 2019

- [Office 2019 安装激活工具 - Office 2019 Install | 代码黑洞](https://www.cd404.com/16.html)

## Sticky Notes

- [Win10 的 StickyNote 数据的存放路径 | CSDN](https://blog.csdn.net/qq_16118075/article/details/88809464)
- [Windows 10 中的 Sticky Notes 便笺应用的数据在系统中的实际存放路径是什么？ | Microsoft Community](https://answers.microsoft.com/zh-hans/windows/forum/windows_10-files/windows10%E4%B8%AD%E7%9A%84sticky/6834b5b2-a6d0-4248-98e4-839e6f2e3a9a)

## 自动修复

- [自动修复无法修复你的电脑 解决方案 | CSDN](https://blog.csdn.net/Logicr/article/details/88686371)
- [Win10 开机自动修复修复失败无限重启 | 百度经验](https://jingyan.baidu.com/article/ed2a5d1f9f1e7309f7be176a.html)

## 上帝模式

- [![](logo/wechat.svg)Win10 如何开启上帝模式 | 戴尔](https://mp.weixin.qq.com/s/3S0LCo25pnwcbglsfDJJZA)
- 桌面新建文件夹，并命名为：

```
上帝模式.{ED7BA470-8E54-465E-825C-99712043E01C}
```

## 开启 Hyper-V

?> 参见 [![](logo/zhihu.svg)Win10 家庭版中使用 Hyper-V | 知乎](https://zhuanlan.zhihu.com/p/51939654)

将以下代码保存为`hyper-v.cmd`，并以**管理员**身份运行：

```powershell
pushd "%~dp0"

dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt

for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

del hyper-v.txt

Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL
```

- [![](logo/zhihu.svg)Win10 家庭版中使用 Hyper-V | 知乎](https://zhuanlan.zhihu.com/p/51939654)
- [![](logo/zhihu.svg)Win10 自带的 Hyper-V 性能、兼容性和稳定性怎么样？| 知乎](https://www.zhihu.com/question/58179981)


## Gif 录制

- [![](logo/gifcam.png ':size=16')GifCam![](logo/star.svg)](http://blog.bahraniapps.com/gifcam/#download)

## 一些文章

?> **Cmder** 记得安装完在配置`Setting-Startup-Environment`里面加上`set LANG=zh_CN.UTF8`，否则输出的一些中文会乱码

- [![](logo/csdn.ico ':size=16')Windows下，根据端口号杀死进程 | CSDN](https://blog.csdn.net/zh592677127/article/details/18617917)
- [![](logo/wechat.svg)十款 Windows 下必装软件，大大增强工作幸福![](logo/star.svg)](https://mp.weixin.qq.com/s/FspPYeiHF6-bmAClcpAVaw)



