# spring-mvc-http2

## 文档

- [mvc-http2](https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html#mvc-http2)
- [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support)

## JDK 8

- JDK8本身不支持TLS 1.2，但JDK8u252 +和JDK9中支持TLS 1.2，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。

## Tomcat

- 从8.5版开始，Tomcat支持JDK8（使用Tomcat Native）和JDK9（使用JSSE）的HTTP/2，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。
- 从Tomcat 9开始支持Servlet 4.0，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。

