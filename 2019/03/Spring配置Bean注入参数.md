# 1.字面值
字面值即可用字符串表示的值，可以通过<value>标签注入。默认情况下基本数据类型及其封装类，String等类型都可以采取字面值注入的方式。因为Spring容器在内部为字面值提供了编辑器，可以把字面值转化为对应的内部变量，Spring还允许用户自定义编辑器
例子：
```
	<bean id="car" class="com.smart.ditype.Car">
		<property name="brand">
			<value>红旗&amp;CA72</value>
		</property>
	</bean>
```
**遇到XML特殊符合要进行转义处理或者加特殊标签**
# 2.引用其他Bean
```
<ref bean="car"></ref>
```
此处有三个参数可选，分别为bean，local,parent，bean可以引用同一容器或者父容器中的Bean，local只能引用同一容器中的Bean，parent可以引用父容器中的Bean
# 3.内部Bean
要使car Bean只被boss Bean引用不被其他Bean引用，可以使用内部Bean注入
```
	<bean id="boss" class="com.smart.attr.Boss">
		<property name="car">
			<bean class="com.smart.attr.Car">
				<property name="maxSpeed" value="200"/>
				<property name="price" value="20000"/>
			</bean>
		</property>
	</bean>
```
# 4.null值
注入null值要使用null专属标签
```
<property name="brand"><null/></property>
```
# 5.级联属性
```
	<bean id="boss3" class="com.smart.attr.Boss">
		<property name="car.brand" value="奥迪" />
	</bean>
```
这里在Boss类中必须为创建一个Car的实例
# 6.集合类型属性

