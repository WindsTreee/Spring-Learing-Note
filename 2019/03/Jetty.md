Maven配置jetty时，<contextPath>标签用于配置上下文，如果不配置，则使用项目名当作访问根URL，如在实例的方法中，不加此标签访问http://localhost:8000/chapter2/index.html会跳转到登录页，加了后访问http://localhost:8000/bbs/index.html跳转到登录页（标签值为bbs）