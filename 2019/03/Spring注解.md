# 4个注解
### 1.@Component:基本注解，标识了一个受Spring管理的组件
### 2.@Respository：标识持久层组件
### 3.@Service：表示服务层组件
### 4.@C
## restcontroller与controller区别
@RestController为@Controller和@ResponseBody的结合，它可以为前端页面返回json数据，实现前后端分离，但它只能返回数据不能跳转到指定页面，而@Controller只能跳转到指定页面，不能返回数据