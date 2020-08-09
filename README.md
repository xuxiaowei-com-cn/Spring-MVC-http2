# spring-mvc-http2

## 文档

- [mvc-http2](https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html#mvc-http2)
- [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support)

## JDK 8

- JDK8 本身不支持 TLS 1.2，但 JDK 8u252+ 和 JDK 9 中支持 TLS 1.2，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。

## Tomcat

- 从 8.5 版开始，Tomcat 支持 JDK 8（使用Tomcat Native）和 JDK 9（使用JSSE）的 HTTP/2，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。
- 从 Tomcat 9 开始支持Servlet 4.0，参见 [HTTP-2-support](https://github.com/spring-projects/spring-framework/wiki/HTTP-2-support) 。

