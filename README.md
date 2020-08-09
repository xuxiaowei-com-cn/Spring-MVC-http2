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
                - 设置为 jdk 1.8
            
            - Project language level
                - 设置为 jdk 1.8

        - Modules
            - 项目名
                - Sources
                    - Language level
                        - 设置为 jdk 1.8
                
                - Dependencies
                    - Modele
                        - 设置为 JDK 1.8

## 文档

- [mvc-http2](https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html#mvc-http2)
- [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support)

## 创建 SSL 文件

- [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/keytool.html)
    - keytool -help
    - 密钥和证书管理工具
    
    - genkeypair
        - keytool -genkeypair -help
        - 生成密钥对
    
            - alias
                - 要处理的条目的别名
        
            - keyalg
                - 密钥算法名称
        
            - validity
                - 有效天数
            
            - keystore
                - 密钥库名称
            
            - storepass
                - 密钥库口令

- 生成密钥对

~~~
keytool -genkeypair -alias spring-boot-http2 -keyalg RSA -validity 3650 -keystore spring-boot-http2.jks -storepass xuxiaowei
~~~

- JKS 密钥库使用专用格式。建议使用 "keytool -importkeystore -srckeystore spring-boot-http2.jks -destkeystore spring-boot-http2.jks -deststoretype pkcs12" 迁移到行业标准格式 PKCS12。

~~~
keytool -importkeystore -srckeystore spring-boot-http2.jks -destkeystore spring-boot-http2.jks -deststoretype pkcs12
~~~

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
