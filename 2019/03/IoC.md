# IoC(Inverse of Control 控制反转)和DI(Dependency Injection 依赖注入)是对同一事物的描述
依赖注入是从应用程序的角度在描述：应用程序依赖容器创建并注入它所需要的外部资源；而控制反转是从容器的角度在描述：容器控制应用程序，由容器反向的向应用程序注入应用程序所需要的外部资源
# IoC的3种注入类型：
## 1.构造函数注入(Spring支持)
> MoAttack类：
```
public class MoAttack {
	private GeLi geli;
	public MoAttack(GeLi geli){
		this.geli=geli;
	}
	public void cityGateAsk(){
		geli.responseAsk("开门！");
	}
}
```
> Direct类：
```
public class Director{
	public void direct(){
		GeLi geli = new LiuDeHua();

		MoAttack moAttack = new MoAttack(geli);
		moAttack.cityGateAsk();
	}

}
```
这样Director类实现了角色选择（LiDeHua）和剧本中角色扮演的解耦

## 2.属性注入(Spring支持)
因为在构造函数注入中选择角色在MoAttack的构造方法里面，但是不是每一个场景都有LiDeHua出场的，所以最好采用Setter方法进行注入较好，这就是属性注入
> MoAttack类：
```
public class MoAttack {
	private GeLi geli;

	public GeLi setGeli(GeLi geli){
		this.geli=geli;
	}

	public void cityGateAsk(){
		geli.responseAsk("开门！");
	}
}
```
> Direct类：
```
public class Director{
	public void direct(){
		MoAttack moAttack = new MoAttack();
		
		GeLi geli = new LiuDeHua();
		moAttack.setGeli(geli);   //进行属性注入
		moAttack.cityGateAsk();
	}
}
```

## 3.接口注入(一般不采用，Spring不支持)