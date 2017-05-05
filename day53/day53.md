# day53

标签（空格分隔）： 每日计划

---
##时间--2017年5月04号

###学习时间<br>
>关于ListView多种类型的item,今天讨论的一个问题就是当我有两种类型的时候,如果我的第一种类型很多,那么这个时候我们的

一般多种类型代码:
```
switch(type){
    if(convertView == null){
        case 0:
            创建holder0; 然后setTag(); 布局控件查找
            break;
        case 1:
            创建holder1; 然后setTag();布局控件查找
            breadk
        default:
            break;
    } else {  //convertView不为空
          case 0:
            getTag();  设置值
            break;
        case 1:
            getTag();  设置值
            breadk
        default:
            break;
    }
}
```
可以想下,当我们的第一个item创建了很多,也就是满足了convertView不为空,及复用的形式之后,这个时候我们创建了第二个item,那么按理说convertView也不为空,但是这个时候convertView确实为空,会不会导致bug呢,但是我们的实际中确实没有崩溃,这个是为什么呢,经过测试,当新一个item的时候,convertView默认为空,那么是谁给置空的呢。我们可以看到有个方法
```
getViewTypeCount()

added in API level 1
int getViewTypeCount ()
Returns the number of types of Views that will be created by getView(int, View, ViewGroup). Each type represents a set of views that can be converted in getView(int, View, ViewGroup). If the adapter always returns the same type of View for all items, this method should return 1.
可以看到,调用getView()这个方法之前都会去调用getViewTypeCount(),如果有新的类型,那么会把convertView置为空,这个时候就解除了我们上面的疑虑。

This method will only be called when the adapter is set on the AdapterView.
```

###阅读文章<br>


###工作<br>


###美好句子<br>
