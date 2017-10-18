# JavaScript 是按值传递还是按引用传递的


### 答案是肯定的，按值传递。

JS所有的函数参数的传递都是按值传递的，而引用类型传递的也是一个值（指向堆内存中的对象的指针副本），这里只说引用类型的传递。


先给大家看一个比较常见的，让人误解为引用传递的。

```
function changeObj(o){
    o.name = "changeobj";
}
var p = {};
changeObj(p);
console.log(p.name);
```

看到这里大家肯定会认为这是按引用传递的啊，因为在函数内部添加了对象的属性，在外边也添加了。那么接下来再看这个例子。


```
var o = {
    name : 'tt'
}
             
var b = new Object();
b.name = 'b';
o = b;
console.log(o.name);
```

 上述代码先创建了一个对象，然后将其赋值非变量o，接着又用构造器创建了一个对象，并修改其属性，然后将其复制给变量对象o，然后访问o的时候name被修改为b了。这里o的引用指向了新对象b;

 再看下面这个例子大家就可以明白了
```
function quoteFn(obj){
    var o = new Object();
    obj = o;
    obj.name = "tony";
    obj.age = 24;
    obj.sex = "Men";
}
 
var person = {
    name : "miracle",
    age : 12
}
 
 
console.log(person.name);
console.log(person.age);
console.log(person.sex);
```

在这个例子中先创建了person对象，并设定其name 属性值为"miracle",age属性值为 12。接着调用quoteFn()函数，并将person对象的值(这里说的是值，这个值是一个指向person对象的指针)传递给了参数obj。

然后在quoteFn函数中穿件了一个局部对象o，并将其复制给了参数obj，然后添加了新的几个属性。最后我们打印person.name 发现属性没有改变。如果是按引用传递，那么person应该指向新的对象啊。

所以综上所述，JS参数的传递是按值传递的，引用类型传递是一个指针的副本。