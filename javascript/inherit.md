### 原型及原型链

* 构造函数

构造函数的执行过程

1. 当以new关键字调用时，会创建一个新的内存空间，标记为Animal的实例

2. 函数体内部的this指向该内存

3. 执行函数体内的代码：给this添加属性，即给实例添加属性

4. 默认返回this[新创建的内存空间]

* 原型对象

当一个函数创建好之后，都会有一个prototype属性，这个属性值是一个对象，我们把这个prototype属性所指向的内存空间称为这个函数的原型对象。

只要在这个原型对象上添加属性和方法，这些属性和方法都可以被改函数的实例所访问。

某个函数的原型对象会有一个constructor属性，这个属性指向该函数本身。

当某个函数当成构造函数来调用时，就会产生一个构造函数的实例。这个实例拥有一个__proto__属性，这个属性指向该实例的构造函数的原型对象。

![原型](../images/prototype.png)

* 原型

所有的引用类型(数组、对象、函数)，都具有对象特性，即可自由扩展属性(null除外)。

所有的引用类型(数组、对象、函数)，都有一个__proto__属性，属性值是一个普通的对象。

所有的函数，都有一个prototype属性，属性值是一个普通的对象。

所有的引用类型(数组、对象、函数)，__proto__属性值指向它的构造函数的prototype属性值。

* 原型链

链式结构

* 判断条件

object instanceof constructor运算符用来测试一个对象在其原型链是否存在一个构造函数。

object instanceof constructor判断的是constructor.prototype是否存在于object的原型链中。

prototypeObj.isPrototypeOf(object)方法用于测试一个对象是否存在于另一个对象的原型链上。

prototypeObj.isPrototypeOf(object)判断的是prototypeObj对象是否存在于object对象的原型链之中。

* 继承

ES5继承：子类先创建属于自己的this，然后再将父类的方法添加到this(也就是使用Parent.apply(this)的方式)或者this.__proto__(即Child.prototype=new Parent())

ES6继承：创建父类的实例对象this，然后再用子类的构造函数修改this

#### 继承

````
function Animal(){
    this.species = 'Animal';
}
function Cat(name){
    this.name = name;
}
````

* 构造函数

使用call或apply方法，把父对象的this指向子对象

缺点: 不能继承原型上的属性和方法

````
function Cat(name) {
    Animal.apply(this, arguments);
    this.name = name;
}
````

* prototype模式

把子对象的prototype对象指向Animal的一个实例

缺点: 如果子对象的prototype对象上有属性或方法时，将被清除

````
Cat.prototype = new Animal();
Cat.prototype.constructor = Cat;
````

* 直接继承prototype

优点: 与prototype模式相比，效率比较高，比较省内存

缺点: 

如果子对象的prototype对象上有属性或方法时，将被清除

Cat.prototype和Animal.prototype现在指向了同一个对象，那么任何对Cat.prototype的修改，都会反应到Animal.prototype

````
Cat.prototype = Animal.prototype;
Cat.prototype.constructor = Cat;
````

* 利用空对象作为中介

F是空对象，所以几乎不占内存。这时，修改Cat的prototype对象，就不会影响到Animal的prototype对象。

缺点: 如果子对象的prototype对象上有属性或方法，将被清除

````
var F = function(){}
F.prototype = Animal.prototype;
cat.prototype = new F();
Cat.prototype.constructor = Cat;
````

* 拷贝继承

优点: 如果子对象的prototype对象上有属性或方法时，不会被清除；子对象的prototype对象修改后父元素的prototype不会被修改

缺点: 只能继承原型上的属性和方法

````
function extend2(Child, Parent) {
    var p = Parent.prototype,
        c = Child.prototype;
    for (var i in p) {
        c[i] = p[i]
    }
}
````

#### inherit的实现

````
function inherit(p) {
    if (p == null) throw TypeError();
    if (Object.create) return Object.create(p);
    var t = typeof p;
    if (t !== 'object' && t !== 'function') throw TypeError();
    function f(){}
    f.prototype = p;
    return new f();
}
````



