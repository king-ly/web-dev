一、启动
docker-compose up -d 

二、登录地址和用户名密码
promethus: http://192.168.99.124:9090/
granfa: http://192.168.99.124:3000/    admin / admin


三、granfa中添加promethus
configuration/Data sources   点击 add data sources
选择promethus填写url地址：
promethus: http://192.168.99.124:9090


四、添加插件 
https://grafana.com/grafana/dashboards?src=grafana_plugin_list
dashboards/import
node: 8919
mysql: 7362
jvm: 4701    给tomcat\springboot用


五、需要动态配置
1、添加jvm监控，根据实际业务IP配置
- job_name: 'springboot_prometheus'
    scrape_interval: 5s
    metrics_path: '/actuator/prometheus'
    static_configs:
    #这里的地址为本机ip
      - targets: ['192.168.32.42:8090']
	  
2、mysql-exporter 需要指定到ip和用户名密码
在docker-compose.yml配置文件中：
  mysql-exporter:
	image: prom/mysqld-exporter
	hostname: mysql-exporter
	#restart: always
	ports:
		- "9104:9104"
	environment:
		- DATA_SOURCE_NAME=root:pzkj13061303@(192.168.99.124:3306)/
		
3、dingtalk的配置需要按实际情况
  dingtalk:
	image: timonwong/prometheus-webhook-dingtalk
	hostname: dingtalk
	#restart: always
	ports:
		- "8060:8060"
	command: 
		--ding.profile="webhook1=https://oapi.dingtalk.com/robot/send?access_token=047c161899fedbf7f75b0e7cd03a6f44b048ee56ce9ac1e848aa4c852bcf652d"
            