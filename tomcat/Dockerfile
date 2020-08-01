FROM registry.cn-huhehaote.aliyuncs.com/pinzhi/tomcat:latest

ENV CATALINA_OPTS="-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005"

EXPOSE 8080
CMD ["catalina.sh", "run"]