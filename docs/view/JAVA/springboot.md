# springboot

## yaml和properties文件内的使用格式

**yaml语法：**

```
#对空格要求非常高
#普通的key-value
#可以注入到配置类中！

server： 
port: 8081
servlet: 
context-path: /mango

#对象
student: 
 name: spring
 age: 3
 
#行内写法
student: {name: spring,age: 3}

#数组
pets: 
  - cat
  - dog
  - pig
  
 pets: [cat,dog,pig]

```



**properties语法:**

```
#properties只能保存键值对！

name=spring

student.name=spring
student.age=3
```

