## Boot

1. 现在安装 → 我没有产品密钥 → Windows 10 专业版 → 自定义：仅安装Windows（高级） → 选择目标驱动器 → 格式化 → 新建
2. 我没有Internet连接
3. 继续执行有线设置
4. 使用脱机账户 → 不填写密码
5. 运行 → `control userpasswords2` → 属性 → 要使用本计算机，用户必须输入用户名和密码(Off)

## Default system environment 

```sh
SET
```

```
# BaseDirs
ALLUSERSPROFILE=C:\ProgramData
APPDATA=C:\Users\User\AppData\Roaming
CommonProgramFiles(x86)=C:\Program Files (x86)\Common Files
CommonProgramFiles=C:\Program Files\Common Files
DriverData=C:\Windows\System32\Drivers\DriverData
HOMEDRIVE=C:
HOMEPATH=\Users\User
LOCALAPPDATA=C:\Users\User\AppData\Local
ProgramData=C:\ProgramData
ProgramFiles(x86)=C:\Program Files (x86)
ProgramFiles=C:\Program Files
PUBLIC=C:\Users\Public
SystemDrive=C:
SystemRoot=C:\Windows
TEMP=%SystemRoot%\TEMP # TEMP=C:\Users\User\AppData\Local\Temp
TMP=%SystemRoot%\TEMP # TMP=C:\Users\User\AppData\Local\Temp
USERNAME=User
USERPROFILE=C:\Users\User
windir=%SystemRoot%
```

```
# Other
ComSpec=C:\Windows\system32\cmd.exe
FPS_BROWSER_APP_PROFILE_STRING=Internet Explorer
FPS_BROWSER_USER_PROFILE_STRING=Default
PATHEXT=.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
```

```
# PATH
Path=C:\Windows;C:\Windows\system32;C:\Windows\System32\OpenSSH;C:\Windows\system32\wbem;C:\Windows\System32\WindowsPowerShell\v1.0
```

## Config

- `Win+Q`
	- 搜索权限和历史记录 → (All Off)
	- Windows Search设置 → 高级搜索索引器设置 → 经典 → 在此自定义搜索位置 → 修改 → 包含的位置/用户 Off → 确定
- 鼠标
	- 鼠标设置 → 其他鼠标选项 → 指针 → Grey Tango
	- 自定义 → 文本选择 → 浏览 → `cursor_white/Text.cur` → 应用
- SMB
	- 启用或关闭Windows功能 → SMB1.0/CIFS文件共享支持(On) → SMB直通(On)
	- 网络和共享中心 → 高级共享设置 → 专用 → 启用网络发现(On) → 启用网络连接设备的自动设置(On) → 启用文件和打印机共享(On)
	- 计算机管理 → 本地用户和组 → 用户 → 右键 → 新用户 → 用户名() → 用户不能更改密码(On) → 密码永不过期(On) → 新建
	- 文件夹 → 右键 → 属性 → 共享 → 共享 → 选择要与其共享的用户 ... 权限级别(读取/写入) → 共享 → 完成
- 查询本机IP
	- CMD → `ipconfig | findstr /i "ipv4"`
	- 网络状态 → 更改适配器选项 → 以太网 → 属性 → Internet协议版本4 → IPv4
- 添加网络位置
	- 此电脑 → 右键 → 添加一个网络位置 → 下一页 → 选择自定义网络位置 → 查看示例 ... 用户名() → 下一步 ... 保存密码(On) → 登录 → 完成
- 新建防火墙规则
	- 管理Windows防火墙规则 → 创建新规则 → 新增空白规则 ... 此程序 → 浏览名称 → 方向 → 出站
- 资源管理器
	- 查看 → 选项 → 常规 → 打开文件资源管理器时打开(此电脑) → 在"快速访问"中显示常用文件夹(Off)
	- ... 查看 → 显示隐藏的文件、文件夹和驱动器 (On) → 隐藏已知文件类型的扩展名 (Off)
- 自动播放CD或其他媒体
	- 可移动驱动器 → 不执行操作
- 关闭Windows键热键
	- 编辑组策略 → 用户配置 → 管理模板 → Windows组件 → 文件资源管理器 → 关闭Windows键热键 → 右键 → 编辑 → 已启用 → 确定
- 键盘
	- Windows
		- 编辑语言和键盘选项
			- 拼写、键入和键盘设置 → 全部关闭
			- 添加语言 → 英语(美国)
			- 替代默认输入法 → 英语(美国) - 美式键盘 → 允许我为每个应用窗口使用不同的输入法 Off
- 声音
	- 声音 → 声音控制面板 → 声音 → 声音方案 → 无声
- Game bar
	- 游戏 → Game Bar (Off) → 允许控制器打开Game Bar (Off)
- 更改DNS服务器
	- 查看网络连接 → 以太网 → 属性 → 网络 → Internet协议版本4 → 属性 → 自动获得DNS服务器地址
	- 命令提示符 → `ipconfig /flushdns`
- 打印机
	- 属性 → 共享 → 共享这台打印机 (On) → 在客户端计算机上呈现打印作业 (On)