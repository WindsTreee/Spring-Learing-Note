### web.xml配置中servlet-class地址为src中的包地址
# 方法
### request.getParameterMap()
此处request是HttpServletRequest类型：
返回一个Map类型的值，该值记录了前端页面提交请求中请求参数与请求参数值的映射关系
### request中各种得到路径方法总结
1. getServletPath():获取能够与“url-pattern”中匹配的路径，注意是完全匹配的部分，*的部分不包括。 
2. getPageInfo():与getServletPath()获取的路径互补，能够得到的是“url-pattern”中*d的路径部分 
3. getContextPath():获取项目的根路径 
4. getRequestURI:获取根路径到地址结尾 
5. getServletContext().getRealPath(“/”):获取“/”在机器中的实际地址 
6. getScheme():获取的是使用的协议(http 或https) 
7. getProtocol():获取的是协议的名称(HTTP/1.11) 
8. getServerName():获取的是域名(xxx.com) 
9. getLocalName:获取到的是IP
[参考链接](https://blog.csdn.net/qq_27770257/article/details/79438987 )
### 重定向时的路径一定要带项目名称，例如：req.getContextPath()+"/msg.jsp"
## 转发（如：req.getRequestDispatcher(msg).forward(req, resp)）则不用

### Servlet生命周期：init()->service()->destory() 
一个servlet在服务器上只有一个实例存在