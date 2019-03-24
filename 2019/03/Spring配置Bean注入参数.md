# 1.字面值
字面值即可用字符串表示的值，可以通过<value>标签注入。默认情况下基本数据类型及其封装类，String等类型都可以采取字面值注入的方式。因为Spring容器在内部为字面值提供了编辑器，可以把字面值转化为对应的内部变量，Spring还允许用户自定义编辑器
例子：
```
	<bean id="car" class="com.smart.ditype.Car">
		<property name="brand" value="红旗&amp;CA72"/>
		<property name="maxSpeed" value="200"/>
		<property name="price" value="20000.00"/>
	</bean>
```