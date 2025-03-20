程序后端由 tp5框架开发 前后端通讯采用 websocket   

所需环境 
宝塔
Nginx
PHP7.1 -- 7.3
Mysql5.7
Redis

程序分为 总控 和 站点后台
注意：宝塔绑定的所有域名应为泛解析   如 *.url.com

1. 上传程序文件 配置伪静态（按照tp程序搭建流程即可）
2. 正常导入并配置数据库   config\database.php
3. 配置 redis    config\redis.php
4. 运行workerman服务 (linux 下 CD至网站目录 php start.php start -d) windows 下 运行 start_for_win.bat
5. 运行workerman 时如果提示PHP函数禁用，则取消即可  参考 https://www.workerman.net/doc/workerman/faq/disable-function-check.html
pcntl_fork
pcntl_wait
pcntl_signal_dispatch
pcntl_signal
pcntl_alarm

6. /houtai 访问总控 admin 123456
7. 总控开通站点，即可访问（开通站点最少需要两个顶级域名，且为泛解析）
8. 总控设置 TG Webhook
url 需开通ssl 例如  https://abc.com/
token 为 tg机器人token
9. 须在 application/index/controller/tg.php 中同时配置 tg机器人token（28行）

总控后台 /houtai
站点后台 /admin/login?token=站点后缀
