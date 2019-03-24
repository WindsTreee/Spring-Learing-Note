### 注意：Spring中基于XML配置Bean时Bean的id必须是唯一的，name可以不唯一
# 1.属性注入配置
Car类中有三个方法，分别为**setBrand(),setMaxSpeed(),setPrice()**

**不使用p命名空间配置**
```
	<bean id="car" class="com.smart.ditype.Car">
		<property name="brand" value="红旗&amp;CA72"/>
		<property name="maxSpeed" value="200"/>
		<property name="price" value="20000.00"/>
	</bean>
```
**使用p命名空间**
```
    <bean id="car" class="com.smart.ditype.Car"
      p:brand="红旗&amp;CA72"
      p:maxSpeed="200"
      p:price="20000.00"/>
```
Spring只会检查调用的类中是否有Setter方法，不检查是否有对应该方法的成员变量
PS：一般建议变量名满足前两个字母大小写一致，方便配置
# 2.构造函数注入配置
**按类型匹配入参**
```
<bean id="car1" class="com.smart.ditype.Car">
		<constructor-arg type="java.lang.String">
			<value>红旗CA72</value>
		</constructor-arg>
		<constructor-arg type="double">
			<value>20000</value>
		</constructor-arg>
	</bean>
```
