## 服务器安装SSH Server 
### WindowsServer 2019
1. 下载SSH
打开PowerShell
```
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'
```
应该返回
```
Name  : OpenSSH.Client~~~~0.0.1.0
State : NotPresent
Name  : OpenSSH.Server~~~~0.0.1.0
State : NotPresent
```
我们选择安装OpenSSH.Server
```
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```
2. 启动服务
```
Start-Service sshd
Set-Service -Name sshd -StartupType 'Automatic'
```
3. 设置防火墙
```
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

###  WindowsServer 2016
1. server 2016就没那么方便了，手动下载：https://github.com/PowerShell/Win32-OpenSSH/releases
2. 解压缩后打开文件夹，修改```sshd_config_default```(默认的里面配置都是注释的)
```
Port 22
PasswordAuthentication yes
```
3. 启动服务
运行目录下的文件```install-sshd.ps1```
设置为自动启动
```
Set-Service -Name sshd -StartupType 'Automatic'
```

4. 设置防火墙
```
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

## 客户端连接
我们以PowerShell为例，命令是这样的：
```
# ssh admin@192.168.0.100
ssh username@servername
```
然后根据提示输入密码就好。

连接上之后，默认使用的是cmd，所以你输入一些```ls```等命令会不识别   
设置默认shell为PowerShell   
```
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force
```

## VS Code远程连接
1. 原理  
![vscoderemote](https://code.visualstudio.com/assets/docs/remote/remote-overview/architecture.png)
2. 下载```Remote -SSH```插件
3. Press F1 and run the Remote-SSH: Open SSH Host... command.
4. Enter your user and host/IP in the following format in the input box that appears and press enter: user@host-or-ip or user@domain@host-or-ip
5. If prompted, enter your password (but we suggest setting up key based authentication).
6. After you are connected, use File > Open Folder to open a folder on the host.

## 参考文档
https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_overview