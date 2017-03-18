# nginx相关

## nginx命令
1.nginx (启动,mac电脑下nginx命令自动集成到根目录下了，不需要切换到安装目录去启动。)
2.nginx -s  stop (停止)
3.nginx -h (nginx帮助，可以查看配置文件地址)
![](/images/1-3.png)

## nginx配置
1.在nginx上配置跨域项
	#跨域配置
	add_header Access-Control-Allow-Origin *;
	add_header Access-Control-Allow-Headers Origin,X-Requested-With,Content-Type,Accept;
	add_header Access-Control-Allow-Methods POST,GET,OPTIONS,DELETE;

2.在nginx上配置转向
	server {
	    listen       8088;
	    error_page   405 =200 @405;

	    location ~ \.(action1)?$ {
		    proxy_pass http://172.31.1.200:3000;
		    proxy_set_header  Host $host;
		    proxy_set_header  X-Real-IP  $remote_addr;
	   }

	    location ~ \.(jsp|jspx|action|json)?$ {
	             proxy_pass http://172.31.3.171:8080; #转向tomcat处理
	             proxy_set_header  Host $host;
	             proxy_set_header  X-Real-IP  $remote_addr;
	    }
	}
场景：我本地系统访问171服务器，端口号8088。如果是正常的接口请求，则重定向到tomcat服务器8080，如果是测试服务，则重定向到测试服务200的3000接口。
