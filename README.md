# JavaStudy

## 一、ArrayList容器

​	List< String > list1 = new ArrayList<>();

​	List<类名> 对象名 = new ArrayList<>();

​	泛型

理论上，ArrayList可以存放任何类型的数据，但是出现以下情况时：

​	List arrayList = new ArrayList();

如果arrayList.add("1234")后又arrayList.add(1234)会出现编译错误，所以在使用ArrayList容器的时候最好指定存放的类型

## 二、for循环

### 1.foreach循环

代码示例：

​	List< String > list1 = new ArrayList<>();

​	for(String item : list1){

​		System.out.println(item);

​	}

### 2.计数遍历

代码示例：

​	for(int index=0;index<list1.size();index++){

​		String item = list1.get(index);

​		System.out.println(item);

​	}

## 三、Date包

### 1.Date包的引用：import java.util.Date

### 2.Date包的应用：

​	Date day1 = new Date();

​	day1.getTime();//返回当前毫秒数

​	SimpleDateFormat adf = new SimpleDateFormat(pattern: "yyyy-MM-dd HH:mm:ss");

​	System.out.println("当前时间："+sdf.format(day1));//将当前时间以标准格式输出，其中的yyyy-MM-dd HH:mm:ss也可以换成yyyy/MM/dd HH:mm:ss，可以自定义格式

​	try{

​		Date day2 = sdf.parse(source:"1988/05/03 15:23:12");

​		System.out.println(sdf.format(day2));

​	}catch(Exception e){

​		e.printStackTrace();

​	}//将字符串时间转换为标准格式时间，try catch为一个抛异常操作

### 3.时间先后顺序的比较

因为一般不存在两个时间的毫秒数也一样的情况，所以Date包中提供了before和after函数用来比较两个时间的先后顺序

​	System.out.println("day1在day2之前："+day1.before(day2));

​	System.out.println("day1在day2之前："+day1.after(day2));

当要比较两个时间是否相等时，我们可以比较他们的毫秒数是否相等：

​	long day1Time = day1.getTime();

​	long day2Time = day2.getTime();

​	System.out.println("day1是否与day2一致："+(day1Time == day2Time));

## 四、Java中的常量

常量一般写在类中，方法体外，格式如下：

​	public ststic final 类型 常量名 = 常量值;

一般常量值要求全部大写，也可加入下划线，如：DOG_COLOR

​	
