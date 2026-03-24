# OpenClaw-Tutorial
## 1、openclaw AI助手windows电脑安装部署及配置微信聊天对话详细教程


openclaw是目前最火爆的开源应用，没有之一，它功能强大远超同类应用。以前AI只是你问它答，OpenClaw可以说是有了手，可以帮你做事，做很多事，如果利用的好，绝对是个利器。下面分享一下windows系统电脑本地安装部署教程，有时候可能会不在电脑前，这里我们配

置一下微信通道，通过微信和OpenClaw交流，来查看它的任务状态或是向它发送任务指令。

准备工作，大语言模型的API key，OPENAI，Gemini，DeepSeek等都可以，没有可以去申请一个key，点击申请：https://s.c1ns.cn/pciqO

一个企业微信号，如果你不打算通过手机操控openclaw的话，可以跳过微信配置这部分。

普通个人微信号也是可以用，但是可能会被风控，所以建议还是用企业微信号，100%安全。

打开企业微信:work.weixin.qq.com

点击页面按钮【立即注册】，页面信息自己随便填就行，不需要上传营业执照，也不需要填写银行卡等信息。

企业微信注册完成后，再下载个企业微信APP，登录上，等下会用企业微信扫码创建机器人。

OpenClaw安装配置

首先安装node.js，下载链接



https://nodejs.org/dist/v24.14.0/node-v24.14.0-x64.msi

全程保持默认安装即可。

安装 OpenClaw

打开cmd终端窗口运行下面命令



npm install -g openclaw@latest

执行引导程序



openclaw onboard --install-daemon

窗口里会显示安全协议说明等信息，反正你得用，不用管，直接敲击键盘y，确定

<img width="846" height="281" alt="image" src="https://github.com/user-attachments/assets/4d2b9f46-229a-437a-a380-5ccbdcf8d065" />


然后选择Onboarding mode，有OpenAI等官方API或以前配置过API环境变量的话，可以选择QuickStart，这里以Manual模式演示。选择第二个Manual，回车

<img width="853" height="184" alt="image" src="https://github.com/user-attachments/assets/c9234930-84c9-41eb-a426-c3399b4eff57" />


网关里选择第一个本地模式

<img width="633" height="69" alt="image" src="https://github.com/user-attachments/assets/2864cb2b-d54f-4569-ab4d-e8f34546e186" />


Workspace directory工作区目录默认C盘，直接回车保持默认，如果你想存储在其它盘符，直接输入文件夹路径即可。

设置Model/auth provider，选择倒数第五个Custom Provider，回车

<img width="465" height="547" alt="image" src="https://github.com/user-attachments/assets/96889b66-09cc-4d42-a7eb-e7da00a7476e" />


API Base URL 大模型的BaseURL，输入



https://api.modelverse.cn/v1/

还没API Key的话可以自己申请，点击申请API：https://s.c1ns.cn/pciqO

接着选择API填写方式，选第一个现在粘贴

<img width="554" height="59" alt="image" src="https://github.com/user-attachments/assets/8cbe69a0-78d7-4b30-9392-779e85299fd2" />


复制API key，在【API Key (leave blank if not required)】下面鼠标右键单击直接粘贴

Endpoint compatibility保存默认第一个OpenAI-compatible，我们用的都是兼容OPENAI模式的API

Model ID模型名输入



deepseek-ai/DeepSeek-V3.2

DeepSeek-V3.2这个模型是兼具性能与价格优势，我比较喜欢用这个模型，智能程度很高，而且很便宜。

回车之后会输出API的验证情况，如果输出“Verification successful.”，那么就说明你的API信息填的正确，如果没输出这个，那么就检查一下你填的是否错误

<img width="245" height="128" alt="image" src="https://github.com/user-attachments/assets/de436069-1c67-4fd5-a63d-f6580413b678" />


Endpoint ID保持默认，直接回车

Model alias (optional)默认，直接回车

Gateway port保持默认，直接回车

Gateway bind选第一个Loopback (127.0.0.1)

Gateway auth选择第一个Token

Tailscale exposure选择第一个OFF

How do you want to provide the gateway token?选第一个Generate/store plaintext token

Gateway token (blank to generate)直接回车

Configure chat channels now?这里是配置聊天工具，我们选择No，因为我们要用微信

Search provider搜索引擎不适合我们，这里选最下面【Skip for now】

Configure skills now?选No

Enable hooks?选第一个Skip for now，因为很多功能以后你想要的话，可以直接通过聊天对话的方式让OpenClaw自己添加，自己配置。想要它怎么样就对它说

Gateway service runtime保持默认，回车，配置完成

Gateway service already installed选第一个Restart，重启服务

这时应用会自动打开webUI控制台页面，以后你就可以在电脑上打开这个页面查看及使用OpenClaw。

http://127.0.0.1:18789/#token=XXXX

不过你可能会看到一个无法访问的页面，因为你的网关启动失败了。

没关系，先不管

下面配置微信，因为我们主要用的就是微信，其它用户加入你的企业微信组织后，也可以使用你的openclaw。

安装微信插件，在cmd终端窗口，运行下面命令：



npx -y @wecom/wecom-openclaw-cli install --force

等到提示请选择企微机器人接入方式时，选择扫码接入

<img width="404" height="98" alt="image" src="https://github.com/user-attachments/assets/97d2032f-52e6-44d0-a59a-5c5bb640deca" />


如果终端窗口里生成的二维码图片手机无法扫描的话，可以复制二维码下方的链接在浏览器里打开进行扫描

<img width="768" height="465" alt="image" src="https://github.com/user-attachments/assets/3cdb5729-9b29-459e-ac84-7d3ca9ec4759" />


扫码完成，手机上创建并授权完毕后终端窗口里也会提示创建完成。

插件安装完成后网关会自动重启，但是跟上面一样，也会重启失败。

这是windows系统下运行会遇到的问题，不过问题不大。

窗口里提示你：网关重启失败，请手动执行: openclaw gateway restart，不过你不要这样操作

关闭CMD终端窗口，然后再重新打开一个CMD终端窗口，依次运行下面命令：


openclaw gateway stop

openclaw gateway

或是直接下载启动脚本https://pan.quark.cn/s/c92ff770effd

OK，网关启动成功。你可以看到终端窗口里输出了很多蓝色文字信息。

再打开上面的WEBUI页面URL，就能成功打开了。如果你没搞定的话可以联系我帮你部署。

这时你可以在企业微信里向你创建的这个机器人通过聊天发送任务指令了。比如说帮你看看你电脑C盘还剩余多少空间了，稍等片刻机器人就会回复你电脑C盘容量信息。是不是很有意思。

用openclaw去操作一些自动化任务真的很强，因为这不仅仅是像按键精灵那样执行简单重复性的任务，openclaw可以看，会思考，可以执行很多复杂的任务，我也在用着openclaw开发着新项目。openclaw的能力绝对让你大开眼界。

重启电脑后openclaw会自动重启，但是跟上面一样会启动失败。你可以下载我写的启动脚本，就三行代码，不到1KB。

以后每次想要使用的时候直接运行这个启动脚本即可。

如果你让openclaw每天定时自动执行任务，需要电脑开机后就要成功启动。那么可以把这个启动脚本添加到自启动。

按下键盘上的 Win + R 键，打开“运行”窗口。

在里面输入：shell:startup ，然后敲回车。

在打开的启动文件夹中，把启动龙虾.bat 文件复制进去即可。

如需人工帮助联系：https://articles.zsxq.com/id_1tlnx05msvst.html

## 2、windows电脑WSL2下安装OpenClwa及实现开机自动启动详细教程

windows系统原生环境下运行openclaw多少还是会遇到点问题，虽然windows原生环境支持使用，但是WSL2仍是官方最推荐的方式。下面是windows系统电脑安装WSL2及OpenClaw详细教程。

安装 WSL2

以管理员身份打开 Windows 上的 PowerShell（右键开始菜单 -> Windows PowerShell (管理员)），输入以下命令：


wsl --install

这会自动安装 WSL2 和默认的 Ubuntu 发行版。系统提示需要重启电脑，我们重启电脑。

重启电脑后，打开开始菜单，找到 Ubuntu 应用，点击打开它，等待几分钟初始化。

系统会提示你创建一个UNIX username用户名，随便填

然后会让你输入密码，输入密码时，不会显示，输入完成后按键盘回车

提示重复输入新密码，输入，回车继续，创建完成，然后就会进入等待输入状态。

<img width="719" height="316" alt="image" src="https://github.com/user-attachments/assets/650cd795-2eb0-4367-812b-f770fc91eb5e" />

在终端里输入以下命令，确保系统是最新的：


sudo apt update && sudo apt upgrade -y

更新时会提示要输入密码，先输入密码确认，然后开始自动更新。

安装OpenClaw

先安装 Node.js，在 Ubuntu 终端里依次运行下面命令：


curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -

sudo apt install -y nodejs

安装浏览器，如果不做浏览器自动化任务的话，可以不用装

npm install playwright

npx playwright install chromium

如果在以后执行浏览器自动化任务时报错缺少libXXX.so库，直接运行下面命令自动补全：

npx playwright install-deps

安装 OpenClaw

依次运行下面命令安装openclaw，

npm install -g openclaw@latest

openclaw onboard --install-daemon

如果上面命令无法安装的话，运行下面官方推荐一键安装命令：

curl -fsSL https://openclaw.ai/install.sh | bash

或从 GitHub 主仓库安装实时最新版

npm install -g github:openclaw/openclaw#main

如果终端窗口长时间没有变化，打开任务管理器，看看网卡流量，是不是正在下载文件中

如果无法安装的话，先解决你的网络问题。

顺利安装的话，稍后会自动启动引导流程，可以查看文章前半部分描述

引导流程配置完成就可以顺利使用了。

如果想要实现开机自动启动的话，下载我写的一个启动脚本startopenclaw.vbs，鼠标右键单击选择编辑，打开脚本文件，修改最后一行代码：

ws.run "wsl -d Ubuntu -- bash -lc '/home/用户名/.npm-global/bin/openclaw gateway > ~/openclaw.log 2>&1'", 0, False

把【用户名】这几个字，改成上面安装WSL2时你创建的UNIX username用户名，修改完保存关闭

按电脑win+R键，输入：shell:startup，打开启动文件夹后，把这个vbs文件复制进去即可。每次重启电脑时，Openclaw 网关会自动运行。

我CPU是I7，不处理任务时后台虚拟机进程vmmem占用CPU约0.1%，占用内存约2.4G。
