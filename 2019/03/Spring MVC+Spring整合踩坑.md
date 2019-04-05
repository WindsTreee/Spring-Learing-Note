## 1.web.xml中需要配置的有：
1.业务层和持久层的Spring配置文件和listener

2.声明DispatcherServlet

3.通过<servlet-mapping>指定DispatcherServlet匹配的URL模式
**PS：在这个过程中
1.Web层Spring容器将作为业务层Spring容器的子容器，即Web层可以访问业务层的Bean，反之却不行

2.一个web.xml可以配置多个DispatcherServlet，通过<servlet-mapping>的配置让每个DispatcherServlet处理不同的请求（通过不同的name标识不同的DispatcherServlet）**
## 2.DispatcherServlet默认加载的是位于/WEB-INF/<servelt-Name>-servlet.xml的Spring配置文件
如果要自己指定可以在声明Servlet的时候通过<init-param>指定