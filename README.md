# spring-mvc-http2

## IDEA 配置

- File
    - settings
        - Build Execution Deployment
            - Compiler
                - Java Compiler
                    - Pre-mode bytecode version:
                        - Module
                            - 删除本模块的 jdk

    - Project Structure
        - Project
            - Project SDK:
                - 设置为 jdk 14
            
            - Project language level
                - 设置为 jdk 14

        - Modules
            - 项目名
                - Sources
                    - Language level
                        - 设置为 jdk 14
                
                - Dependencies
                    - Modele
                        - 设置为 JDK 14

## 文档

- [mvc-http2](https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html#mvc-http2)
- [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support)

## JDK 8

- JDK8 本身不支持 TLS 1.2，但 JDK 8u252+ 和 JDK 9 中支持 TLS 1.2，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。

## Tomcat

- 从 8.5 版开始，Tomcat 支持 JDK 8（使用Tomcat Native）和 JDK 9（使用JSSE）的 HTTP/2，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。
- 从 Tomcat 9 开始支持Servlet 4.0，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。

## Tomcat 配置

- 将 ssl/spring-boot-http2.jks 放入 tomcat目录/conf/ssl/spring-boot-http2.jks

- 修改 tomcat目录/conf/server.xml
~~~
<Connector port="8443" protocol="org.apache.coyote.http11.Http11NioProtocol"
           maxThreads="150" SSLEnabled="true">
    <UpgradeProtocol className="org.apache.coyote.http2.Http2Protocol" />
    <SSLHostConfig>
        <Certificate certificateKeystoreFile="conf/ssl/spring-boot-http2.jks"
                     type="RSA" certificateKeystorePassword="xuxiaowei"/>
    </SSLHostConfig>
</Connector>
~~~
