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

}

### 2.计数遍历

代码示例：

​	for(int index=0;index<list1.size();index++){

​		String item = list1.get(index);

​		System.out.println(item);

}

​	
