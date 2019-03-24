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

Car中有一个构造函数：
```
	public Car(String brand, double price) {
		this.brand = brand;
		this.price = price;
	}	

```
对应的Bean配置
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
这里Spring根据配置里面的类型自动匹配对应的构造方法

**按索引匹配入参**
假定Car类的构造方法有多个相同类型入参
```
	public Car(String brand, String corp, int maxSpeed) {
		this.brand = brand;
		this.corp = corp;
		this.maxSpeed = maxSpeed;
	}
```
此时根据type就无法判断到底哪个值匹配哪个入参，此时通过索引来确定
```
	<bean id="car4" class="com.smart.ditype.Car">
		<constructor-arg index="0">
			<value>红旗CA72</value>
		</constructor-arg>
		<constructor-arg index="1">
			<value>中国一汽</value>
		</constructor-arg>
		<constructor-arg index="2" type="int">
			<value>200</value>
		</constructor-arg>
	</bean>
```
**按索引和类型匹配入参**
Car有两个构造函数
```
	public Car(String brand, String corp, double price) {
		this.brand = brand;
		this.corp = corp;
		this.price = price;
	}
	public Car(String brand, String corp, int maxSpeed) {
		this.brand = brand;
		this.corp = corp;
		this.maxSpeed = maxSpeed;
	}
```
这里采用索引是不行的，第三个的值若为整数两个构造方法都符合条件，所以要采用联合入参
```
	<bean id="car3" class="com.smart.ditype.Car">
		<constructor-arg index="0" type="java.lang.String">
			<value>红旗CA72</value>
		</constructor-arg>
		<constructor-arg index="1" type="java.lang.String">
			<value>中国一汽</value>
		</constructor-arg>
		<constructor-arg index="2" type="int">
			<value>200</value>
		</constructor-arg>
	</bean>
```
这里引起歧义的是第三个入参，所以前两个的type可以去除

**根据反射机制自动匹配入参**
如果Bean的构造函数入参类型是可辨别的（）

