# This is a Test---->H1
## This is a Test---->H2

**粗体的Test**<br>
*斜体的Test*<br>
~~在Test上添加删除线~~<br>
<br>
* Test1
 * Test1_1
  * Test1_1_1
* Test2
* Test3
1. Test1
2. Test2
3. Test3
  * Test3_1
  * Test3_2
  * Test3_3
***
[My Blog](http://www.bing.com "单击进入bing搜索,哈哈")
> 第一行引用
> 第二行引用

***
`System.out.println("I love android.")`
```Java
public class Test{
 public static void main(String[] args){
   System.out.println("I love android.It is great OS for Mobile");
 }
}
```
##接口：
方法名|参数|描述
------|----|-------
add(a,b)|整型or浮点型|两数相加
sub(a.b)|整型or浮点型|两数相减
***
Test1
Test2
: Test2_1
: Test2_2
> part of Test2_2
> **Note:** You can find more information:
> - about **Test1** hignlighting [here][1].
> - about **Test2** highlighting [here][2].

##About footnotes
you can create footnotes like this[^footnote].
[^footnote]:Here is the *text* of the **footnote**.
***
##截图
![My Pic](https://pic1.zhimg.com/e8a76d91f7182b1b40ce639a3cb7e88c_l.jpg)
##UML图
* 渲染序列图
```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```
* 流程图
```flow
st=>start: Start
e=>end
op=>operation: My Operation
cond=>condition: Yes or No?

st->op->cond
cond(yes)->e
cond(no)->op
```


