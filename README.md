#v2ray 搭建节点整理

更新系统，安装curl/wget等：yum -y install wget    #ContOS 安装 wget

                        apt-get install wget   #Debian Ubuntu 安装 wget
                        
                        yum -y install curl    #ContOS 安装 curl
                        
                        apt-get install curl   #Debian Ubuntu 安装 crul

1.简单搭建-01：bash <(curl -s -L https://git.io/v2ray.sh)

2.简单搭建-02：bash <(curl -sL https://cdn.jsdelivr.net/gh/Misaka-blog/Xray-script@master/xray.sh)

3.SSL搭建，需要域名，可搭建TSL节点（7）：bash <(curl -sL https://storage.googleapis.com/tiziblog/setup.sh)
