## 1.web.xml中需要配置的有：
1.业务层和持久层的Spring配置文件和listener
2.声明DispatcherServlet
3.通过<servlet-mapping>指定DispatchServlet匹配的URL模式
PS：1.在这个过程中，Web层Spring容器将作为业务层Spring容器的子容器，即Web层可以访问业务层的Bean，反之却不行
2.一个web.xml可以配置多个DispatchServlet，通过