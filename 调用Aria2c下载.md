### 6盘小白羊新版已支持配置为调用Aria2c下载6盘文件


#### 下载地址：https://ws28.cn/f/31i7pj8vpzx

因为还没有发布大的版本更新，先打包发布了一个临时的版本，点击上面下载

### 适用于

1. 自己有vps配置了Aria2c，想要使用vps下载（包括进一步配置Rclone之类，实现自动上传到onedrive，googledrive）
2. 自己家里电脑运行Aria2c，然后在公司远程下载（文件下载到家里电脑上）

### 使用步骤

先在【6盘小白羊版Aria.exe】文件的同目录，创建【aria.config】文件，然后再启动【6盘小白羊版Aria.exe】即可<br/>
警告:一定要先创建  aria.config  文件，设置好，再启动  6盘小白羊版Aria.exe  

=========================下面是[aria.config]文件内容=====================<br/>
~~~
#后面是注释
#配置aria服务器完整地址 例如：Server=http://114.114.114.114:6800/jsonrpc
#注意这里   不支持https，不支持ws   必须是http

Server=


#配置aria服务器的秘码 例如：Token=44b11bd2ba34dbebcdb1
#注意这里   不支持为空，必须有密码

Token=

~~~



=========================下面是辅助说明============================<br/>

只有你自己6盘内的文件，才能调用aria下载<br/><br/>
6盘正在离线中的文件，此时并不在你的6盘中，必须等离线成功，显示在你的6盘中，再调用aria下载<br/><br/>
巨大的文件下载超过30分钟时可能会提示下载失败（是因为6盘的下载地址本身有时效），此时直接点击  下载  按钮，重新下载就可以（是自动断点续传的，不会真的重新下载）<br/><br/>
此配置文件只是设置[6盘小白羊版Aria.exe]，并不会修改aria的任何设置，如有特殊需要，请直接修改aria服务器上的配置文件，或自行使用其他第三方UI修改aria的设置（http://aria2c.com，Aria2NG等）<br/><br/>
aria会创建xx.aria的控制文件，是断点续传的需要，文件下载完后可能不会自动删除，需要自己配置on-download-complete的脚本<br/><br/>
aria只支持sha和md5的下载结束后文件校验功能，但6盘采用特殊的hash，导致aria无法支持下载结束后文件校验功能<br/><br/>
调用aria远程下载，可以通过设置Server=http://127.0.0.1:6800/jsonrpc 实现调用本机运行的aria<br/><br/>
[6盘小白羊版Aria.exe]只是调用aria，并不会直接实现自动上传到onedrive，googledrive，需要你自行配置相关的插件，比如  Rclone，OLAINDEX，OneDriveUploader，heroku，oneindex<br/><br/>
我没用过上传到onedrive，googledrive，我只测试了可以正常调用aria服务器下载<br/><br/>
不论是下载速度慢，还是上传速度慢，都不是[6盘小白羊版Aria.exe]的原因，请检查自己的网络或6盘的网络本身导致<br/><br/>
