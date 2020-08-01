# docker
一、安装软件说明

>  1、mysql8.0.20与生产环境相同

>  2、tomcat采用生产环境自建镜像

二、创建HOME下的工作目录workSpace

>  C:\Users\当前用户\workSpace\

>  下载docker-compose工作档：git clone https://gitlab.acewill.cn/pzkj-dev-workspace/docker.git

三、运行docker-compose档
> cd C:\Users\当前用户\workSpace\docker
> docker-compose up -d     


四、开发环境参数修改【web项目】

1、jdbc.properties
注意这里有个参数需要添加 allowPublicKeyRetrieval=true  
```
jdbc_url=jdbc:mysql://虚拟机IP:3306/pinzhicatering?useUnicode=true&characterEncoding=utf-8&serverTimezone=GMT%2B8&allowPublicKeyRetrieval=true&useSSL=false&allowMultiQueries=true
jdbc_username=root
jdbc_password=pzkj13061303
```



2、database.properties
> 添加一个虚拟机IP可访问的配置
```
 192.168.99.122=dataSource
 192.168.99.122.database=pinzhicatering
 192.168.99.122.dbtype=mysql
```



3、configure.properties
> 修改redis的地址和密码
```
redis.host=192.168.99.122
redis.pwd=pzkj13061303
redis.port=6379
```


五、下载DB结构文件
> 链接：https://pan.baidu.com/s/1wfysv1Pzb36jx8DFTaE-pA
> 提取码：aezd

