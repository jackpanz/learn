# kotlin基本数据类型
```kotiln
Double  64
Float	32
Long    64
Int     32
Short	16
Byte    8
```
# 类声明
```kotiln
class A {

}
//可继承的类
open class A {
    //可继承的方法
    open fun v() {}
    //可继承的属性
    open val attr: Int = 1
}
```
### 类构造方法
```kotiln
//相当于constructor(param:String)
class A (param:String){
 //主构造函数
 init{
  println("init")
  println("param:"+param)
 }
}
class A (){
//主构造函数
 init{
  println("init")
 }
 //副构造函数
 constructor(){
 }
}
```
### 多个构造方法
```kotiln
class AA:A{
 init{
  println("init")
 }
 //私有的构造方法
 private constructor(){
 }
 //可以调用父类的构造方法
 constructor(param:String):super(){
 }
 //可以调用本类的其他构造方法
 constructor(param1:String,param2:String):this(param1){
 }
}
```
### 属性
```kotiln
val attr: Int = 0
//getter setter
val attr: Int = 0
    get() {
        println("---get---")
        return field
    }
    set(value) {
        println("---set---")
    }
//属性继承 open声明可继承，override声明继承属性
open val attr: Int = 1
override val attr: Int = 2
//延迟加载 只能修饰,非kotlin基本类型
lateinit val attr: String
```
### 静态变量或常量
```kotiln
class A {
    companion object {
        //静态变量 可以改变
        var URL1: String = "URL1"
        //常量
        val URL2: String = "URL2"
        //常量 相当于加了private和get方法取值
        const val URL3: String = "URL3"
        //常量 懒加载
        val URL4: String by lazy {
            var value:String = URL2 + URL3
            value
        }
    }
}
```

# object 与companion object的区别
### companion object 為此class靜態方法或靜態變量的聲明
### object 直接聲明為全局的靜態類
```kotiln
object A {
    fun aFun() {
    }
}
fun main(args: Array<String>) {
  A.aFun();
}
```
### object 在class裡聲明為此類內部靜態對象，為單例模式
```kotiln
open class B{
    fun bFun(){}
}
class A {
    object b:B();
    object c {
        fun cFun() {}
    }
}
fun main(args: Array<String>) {
    A.c.cFun();
    A.b.bFun();
}
```

# 判斷
//判斷字符是否相等
```kotiln
str1 == str2
str1.equals(str2, false)
//不區分大小寫
str1.equals(str2, true)
```

# 循環
```kotiln
//循環index
for (i in 1..4) print(i) // 打印结果为: "1234"
for (i in 4 downTo 1) print(i)  // 打印结果为: "4321"
for (i in 1..4 step 2) print(i) // 打印结果为: "13"
for (i in 4 downTo 1 step 2) print(i) // 打印结果为: "42"
for (i in 1 until 10) println(i) // i in [1, 10] 不包含 10

//循環數組
val array = arrayOf("苹果", "香蕉", "菠萝")
for (i in array.indices) {
    println(array[i])
}
for ( i in 0 .. array.lastIndex ) {
    println("" + i + ":" + array[i])
}
for ( i in array.lastIndex downTo 0 ) {//倒敘循環
    println("" + i + ":" + array[i])
}

//循環list
val items = listOf("apple", "banana", "kiwi")
for (item in items) {
    println(item)
}
for (index in items.indices) {
    println("item at $index is ${items[index]}")
}
items.forEach { item ->
    println(item)
}
for ( i in items.lastIndex downTo 0 ) {//倒敘循環
    println("" + i + ":" + items[i])
}

//循環map
var map = mapOf<String, Int>("Java" to 86, "Kotlin" to 92, "Go" to 78)
for ((key, value) in map) {
    println(key + ":" + value)
}
map.forEach { key, value ->
    println(key + ":" + value)
}
var iterator = map.keys.iterator();
while (iterator.hasNext()) {
    var key = iterator.next();
    var value = map.get(key);
    println(key + ":" + value)
}

//循環字符串
var str = "1234567"
for(i in str.indices){
    println(str[i])
}
for ( i in 0 .. str.lastIndex ) {
    println("" + i + ":" + str[i])
}
for ( i in str.lastIndex downTo 0 ) {//倒敘循環字符串
    println("" + i + ":" + str[i])
}
```
