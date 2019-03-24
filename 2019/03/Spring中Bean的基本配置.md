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
PS：
