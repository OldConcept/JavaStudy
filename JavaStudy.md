# JavaStudy

## 一、ArrayList容器

```	
List<String> list1 = new ArrayList<>();
List<类名> 对象名 = new ArrayList<>();
```

​	泛型

理论上，ArrayList可以存放任何类型的数据，但是出现以下情况时：

```	java
List arrayList = new ArrayList();
```

如果arrayList.add("1234")后又arrayList.add(1234)会出现编译错误，所以在使用ArrayList容器的时候最好指定存放的类型

## 二、for循环

### 1.foreach循环

代码示例：

```java
List<String> list1 = new ArrayList<>();

for(String item : list1){

	System.out.println(item);

}
```

### 2.计数遍历

代码示例：

```java
for(int index=0;index<list1.size();index++){
	String item = list1.get(index);
	System.out.println(item);	
}
```

## 三、Date包

### 1.Date包的引用：import java.util.Date

### 2.Date包的应用：

```java
Date day1 = new Date();
day1.getTime();//返回当前毫秒数
SimpleDateFormat sdf = new SimpleDateFormat(pattern: "yyyy-MM-dd HH:mm:ss");
System.out.println("当前时间："+sdf.format(day1));//将当前时间以标准格式输出，其的yyyy-MM-dd HH:mm:ss也可以换成yyyy/MM/dd HH:mm:ss，可以自定义格式
try{
	Date day2 = sdf.parse(source:"1988/05/03 15:23:12");
	System.out.println(sdf.format(day2));
}catch(Exception e){
	e.printStackTrace();
}//将字符串时间转换为标准格式时间，try catch为一个抛异常操作
```



### 3.时间先后顺序的比较

因为一般不存在两个时间的毫秒数也一样的情况，所以Date包中提供了before和after函数用来比较两个时间的先后顺序

```java
System.out.println("day1在day2之前："+day1.before(day2));
System.out.println("day1在day2之前："+day1.after(day2));
```

当要比较两个时间是否相等时，我们可以比较他们的毫秒数是否相等：

```java
long day1Time = day1.getTime();
long day2Time = day2.getTime();
System.out.println("day1是否与day2一致："+(day1Time == day2Time));
```

## 四、Java中的常量

常量一般写在类中，方法体外，格式如下：

```java
public ststic final 类型 常量名 = 常量值;
```

一般常量值要求全部大写，也可加入下划线，如：DOG_COLOR

## 五、Stream流操作

### 1.Stream filter是一段数据的序列，如：

```
List<String> strings = Arrays.asList("abc",",","123");
```

### 2.Stream filter过滤操作

```java
List<String> filterd = strings.streams().filter(st->st.startsWith("a")).collect(Collectors.toList());
```

加粗的是过滤规则，可以自己编写，也可以用官方的

## 六、StringBuilder

StringBuilder用于实例化一个可变的字符串对象

```java
StringBuilder sb = new StringBuilder();
sb.append("Hello");
```

StringBuilder对象使用append方法加入字符串

**注意：sb.toString()不能够让sb变成String类型，sb本质还是StringBuilder类型，toString方法只能返回一个String类型的值，当方法需要返回其String类型时，只需要return sb.toString()就行 **

## 七、字符串的比较

```java
boolean s = a.equals(b);//a,b为字符串
```

## 八、枚举类型

### 1.枚举类型的关键字是：enum 其地位与class相同

### 2.所有的枚举值都是常量

### 3.枚举类型不能实例化

示例：

```java
public enum Animal{
    cat,
	tiger,
	dog
}
```

## 九、继承

**继承格式： public class 类名 extends 某个类**

### 父子关系的强制转换

#### 1.子转父： Fruit fruit = apple; (这种关系转换可以直接使用“=”)

#### 2.父转子： Apple apple = (Apple) fruit; (这种关系转换必须使用类型强制转换)

## 十、接口

### 1、定义

同一行为有不同的实现，接口的存在容易拓展更多的实现

**规范：    包名：service**

​				**接口名：以Service结尾**

​				**类型：interface** 

```java
public interface RedPacketService{
public void send(String toUserKey);//注意接口没有{}写实现方法
}
```

### 2、接口的实现

接口的实现是指在特定的场景下实现接口的具体行为(就比如发红包，发红包可以有支付宝发红包，也可以有微信发红包)

**规范：	包名：service.impl**

​				**类名：以ServiceImpl结尾**

```	java
public class AlipayRedPacketServiceImpl implements RedPacketService{
	@Override
	public void send(String toUserKey){
	//这里面写具体的实现方法
}
}
```

### 3、一些注意点

* 一个类可以既有继承的同时也有对接口的实现，规范如下：

  ```java
  public class ClassA extends ClassB implements InterfaceA{}
  ```

  这个格式是必须的，必须先进行继承然后再有接口

* 一个类实现某接口，必须重写该接口下的所有方法(**抽象类除外**)

* java类是单继承的，但java接口可以多继承

  * 一个类只能extends一个父类，但是可以implements多个接口
  * 一个接口可以extends多个接口，但不能implements任何接口

  * 不允许类多重继承的原因是,如果A同时继承B和C，而B和C有同一个方法，那么A就无法确定该继承哪个方法

