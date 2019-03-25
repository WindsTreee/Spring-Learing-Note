```
@Component("userDao")
public class UserDao {
    ...
}
```
与下面的配置语句等价
```
<bean id="userDao" class="com.smart.anno.UserDao" />
```
除了@Component外另外三个与它基本等效的注解
@Repository:用于对DAO实现类进行标注
@Service:用于对Service实现类进行标注
@Controller:
