**Bean的作用域通过配置文件中的scope="xxx"来指定**
# Singleton:单例作用域，每次请求bean都是同一个Bean
# prototype:非单例作用域，每次请求bean都是新的bean，它在容器初始化的时候不创建bean，请求时才创建
# request：作用域对应一个HTTP请求和生命周期
# session：作用域横跨整个HTTP Session
# gloablSession：作用类似于session，但仅在Portlet Web应用中使用