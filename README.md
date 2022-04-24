 搭建节点整理

      安装curl/wget等：   简单：apt-get update && apt-get install wget curl git -y
             
	                 yum -y install wget    #ContOS 安装 wget

                        apt-get install wget   #Debian Ubuntu 安装 wget
                        
                        yum -y install curl    #ContOS 安装 curl
                        
                        apt-get install curl   #Debian Ubuntu 安装 crul

1.简单搭建-01：bash <(curl -s -L https://git.io/v2ray.sh)

2.简单搭建-02：bash <(curl -sL https://cdn.jsdelivr.net/gh/Misaka-blog/Xray-script@master/xray.sh)

3.SSL搭建，需要域名，可搭建TSL节点（7）：bash <(curl -sL https://storage.googleapis.com/tiziblog/setup.sh)

4.隐藏IP搭建：-1-1.Debian/Ubuntu系统执行以下命令(更新系统，安装curl/socat)：

              apt update -y && apt install -y curl && apt install -y socat

                2.CentOS系统执行以下命令：

               yum update -y && yum update -y && yum install -y socat

            -2-运行Acme脚本

               curl https://get.acme.sh | sh

             -3-申请证书及密钥

                 【将代码中注释的邮箱和域名，改为你自己的】

                ~/.acme.sh/acme.sh --register-account -m xxxx@gmail.com

               ~/.acme.sh/acme.sh  --issue -d 输入你的域名  --standalone

            -4-下载证书及密钥

              ~/.acme.sh/acme.sh --installcert -d 输入你的域名 --key-file /root/private.key --fullchain-file /root/cert.crt
      
               端口设置只能为  443

                      证书地址：/root/cert.crt

                      密钥地址：/root/private.key

            -5-安装&升级x-ui面板一键脚本

              bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
              
             -6-BBR加速：
             
                       wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
                       
5.HEROKU搭建

               -1.      https://github.com/bclswl0827/v2ray-heroku
        在网站上找到这个地址（搜索v2ray-heroku)
        点击fork，到自己账户下

               -2.     点击下方README.MD后的修改按键，安装要求修改

         【 Fork 本专案到自己的 GitHub 账户（用户名以 example 为例）
         修改专案名称，注意不要包含 v2ray 和 heroku 两个关键字（修改后的专案名以 demo 为例）
          修改 README.md，将 bclswl0827/v2ray-heroku 替换为自己的内容（如 example/demo）】

               -3.        点击下方DEPLOY TO HEROKU
 
               -4.        在HEROKU 界面中 APP NAME  输入（英文） 然后下拉到最后点击DEPLOY APP  等待安装完成后点击MANAGE APP


               -5.   新页面内点击SETTING
   

               -6.    在Domains后的地址添加至V2中的vmess的地址栏，端口为443，用户ID在网页中Config Vars下的ID，
      额外ID也在网页中Config Vars下的AID，加密方式不变；别名随便填；传输协议ws；
       伪装类型不变；伪装域名不变；路径/；底层安全tls;不支持PING测试，可下载速度测试。

               -7.    加速

     https://dash.cloudflare.com/
     在这个网站右侧，点击Workers;新页面点击创建Worker；新页面输入代码

     addEventListener(
	"fetch",event => {
		let url=new URL(event.request.url);
		url.hostname="域名";
		let request=new Request(url,event.request);
		event. respondWith(
			fetch(request)
		)
	}
     )

    将上面代码内域名改为新申请的网址（Domains后的地址）（不要http://和最后的/）


    点击保存并部署      ------    成功没有报警代码后点击发送       -------------    出现400 Bad Requst则成功

               -8.      复制网址至V2的伪装域名内，利用better-cloudflare-ip选择优选IP，将这个IP输入到V2的地址中。


              结束
              
              
