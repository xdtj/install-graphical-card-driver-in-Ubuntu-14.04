# install-graphical-card-driver-in-Ubuntu-14.04

Ubuntu 14.04 安装 Nvidia 私有驱动并进行双显卡切换

通过nvidia-prime可以在nvidia-settings里手动进行双显卡切换，比如从Nvidia性能模式切换为Intel节能模式。

Ubuntu的私有驱动库restricted里收录了Nvidia官方的图形驱动，我们可以很方便地使用apt-get或者在图形化的Ubuntu软件中心里进行安装：

1 sudo apt-get install nvidia-331 nvidia-settings nvidia-prime
跟Windows一样，安装显卡驱动需要重启才会生效。

Nvidia官网同样为Linux提供有驱动安装程序，比如针对64位Linux的最新稳定版本331： 
http://www.geforce.cn/drivers/results/75062 
不过个人还是建议直接用apt-get进行安装，apt-get会根据系统类型自动选择安装32位还是64位的驱动，而且restricted库里的驱动一般都经过Ubuntu测试，相对来说更稳定，操作起来也更方便。 

Nvidia显卡的控制面板 nvidia-settings的 快捷方式位于/usr/share/applications/nvidia-settings.desktop 
你可以链接一个到桌面，方便进行显卡设置。 
你也可以直接Alt+F2运行 nvidia-settings打开控制面板，比如在Thermal Settings下查看显卡温度，在PRIME Profiles下进行显卡切换。
有了nvidia-prime，就不需要bumblebee了，在Nvidia官方的控制面板nvidia-settings里就可以切换显卡，非常方便。

我在开启Nvidia显卡时GPU温度为40°C，CPU温度为41°C，如下图所示。


在不玩大型3D游戏或者不看高清视频时，建议你从“Nvidia性能模式 ”切换为 “Intel节能模式”。
Intel节能模式下会自动关闭Nvidia显卡，从而实现节能。另外Intel核显自身就有着不错的硬件加速能力，平时使用 Intel核显即可。
比如京东上这款上万元的 MacBook也只是配备了一款i5的CPU并使用Intel核显Iris Graphics进行硬件加速。 
另外很多 超级本也只是配备了Intel低电压版处理器并使用内置的HD Graphics。 
Intel已经把自己的 图形驱动 集成到了Linux内核项目，因此不需要额外安装Intel图形驱动，开箱即用。 
如果长期不需要使用独显，可以开机进BIOS把Graphic Mode由Switchable改为Integrated禁用独显。 

附：你也可以安装VirtualGL进行glxspheres硬件加速测试。
http://sourceforge.net/projects/virtualgl/files/VirtualGL/
比如下载64位的Deb包，安装后运行/opt/VirtualGL/bin/glxspheres64即可进行测试。

Reprinted from:http://my.oschina.net/eechen/blog/227134
