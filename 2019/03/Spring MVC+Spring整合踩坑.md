## 1.web.xml中需要配置的有：
1.业务层和持久层的Spring配置文件和listener

2.声明DispatcherServlet

3.通过<servlet-mapping>指定DispatcherServlet匹配的URL模式
**PS：在这个过程中
1.Web层Spring容器将作为业务层Spring容器的子容器，即Web层可以访问业务层的Bean，反之却不行

2.一个web.xml可以配置多个DispatcherServlet，通过<servlet-mapping>的配置让每个DispatcherServlet处理不同的请求（通过不同的name标识不同的DispatcherServlet）**
## 2.DispatcherServlet默认加载的是位于/WEB-INF/<servelt-Name>-servlet.xml的Spring配置文件
如果要自己指定可以在声明Servlet的时候通过<init-param>指定

## 3.web.xml中若版本是2.3则不支持el表达式，即${}这样的代码无法使用，可以在Project Structure的Module中删除web.xml然后重新添加一个，这样可以选择版本号，或者直接修改配置文件使idea建立web项目时创建的web.xml版本为指定版本
[修改web.xml配置文件](https://blog.csdn.net/senAr59/article/details/80538821)

## 4.前端传递到后端中文乱码问题：因为SpringMVC默认的编码为ISO-8859-1，所以会乱码，最好的解决方式是在web.xml中添加编码过滤器，把所有的数据编码转化成UTF-8
```
    <filter>
        <filter-name>characterEncodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <init-param>
            <param-name>forceEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>characterEncodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```
## 5.@RequestMapping在类处定义的URL是相对于Web应用的部署路径，在方法处定义的URL则是相对于类定义处的URL，如果类处没有定义URL，方法处定义的URL则是直接相对于根路径的。@RequestMapping还支持Ant风格
