## Firewall

#### 添加规则

    firewall-cmd --zone=public --add-port=80/tcp --permanent

#### 重启生效

    firewall-cmd --reload

#### 查询

    firewall-cmd --zone=public --query-port=33378/tcp
    firewall-cmd --list-all
    firewall-cmd --list-all-zones

## 配置 ssh 端口

    vi /etc/ssh/sshd_config

## IP 封禁

    firewall-cmd --permanent --add-rich-rule="rule family='ipv4' source address='222.222.222.222' reject"

修改 port 配置项即可，多个端口配置多个，然后重新启动 sshd 服务即可

**Tips：某些 vps 具备 ipv6 功能，程序可能会运行在 ipv6 端口，小心被坑**

**Tips：jvm 禁用 ipv6 功能 -Djava.net.preferIPv4Stack=true**

启动与停止

    1. 停止
    systemctl stop firewalld.service

    2. 启动
    systemctl start firewalld.service

    3. 重启
    systemctl restart firewalld.service

    4. 查看状态：
    systemctl status firewalld

    5.禁止firewall开机启动
    systemctl disable firewalld

    6. 设置开机启用防火墙：
    systemctl enable firewalld.service

规则与状态

    1. 查看默认防火墙状态（关闭后显示notrunning，开启后显示running）
    firewall-cmd --state

    2. 查看防火墙规则（只显示/etc/firewalld/zones/public.xml中防火墙策略）
    firewall-cmd --list-all

    3. 查看所有的防火墙策略（即显示/etc/firewalld/zones/下的所有策略）
    firewall-cmd --list-all-zones

    4. 重新加载配置文件
    firewall-cmd --reload

常用命令

    查看版本： firewall-cmd --version

    查看帮助： firewall-cmd --help

    显示状态： firewall-cmd --state

    查看所有打开的端口： firewall-cmd --zone=public --list-ports

    更新防火墙规则： firewall-cmd --reload

    查看区域信息:  firewall-cmd --get-active-zones

    查看指定接口所属区域： firewall-cmd --get-zone-of-interface=eth0

    拒绝所有包：firewall-cmd --panic-on

    取消拒绝状态： firewall-cmd --panic-off

    查看是否拒绝： firewall-cmd --query-panic
