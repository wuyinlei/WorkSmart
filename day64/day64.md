# day64

标签（空格分隔）： 每日计划

---
##时间--2017年5月15号

###学习时间<br>
* [深入理解ConstraintLayout之使用姿势][1]
* [Android ConstraintLayout详解][2]
* [Android中，在子线程使用Toast会报错？][3]
* [集成第三方推送最佳实践][4]
* [第三方登录/分享最佳实践][5]

###阅读文章<br>
* [你别来了，我不想谈恋爱了][6]
* [四年了，我爱你！][7]

###每日工作<br>


###GET技能
>1、为了防止在创建TN时抛出异常,需要在子线程中使用Looper.prepare()和Looper
.loop()
2、为了使TN中最终调用Handler对象是基于主线程的,需要使用反射将其替换掉,changeHandlerValue()作用就是这个


```
private void changeHandlerVaule(Object tn){
    try{
        Field mHanderField = tn.getClass().getDeclaredField("mHandler");
        mHanderField.setAccessible(true);
        mHanderField.set(tn,new Handler(Looper.getMainLooper()));
    } catch(Exception ex){
        ex.printStackTrace();
    }
}
```
3、由于ITransientNotification不可见,所有不能通过obj.getClass().getDeclaredMethod("enqueueToast",...)的方法来直接过去到这个Method


  [1]: http://www.jianshu.com/p/b406ddc8b913
  [2]: http://www.jianshu.com/p/a8b49ff64cd3
  [3]: https://www.zhihu.com/question/51099935
  [4]: http://www.jianshu.com/p/d650d02a1c7a
  [5]: https://juejin.im/post/58c21aa944d9040068e71e2c
  [6]: http://www.jianshu.com/p/c8df6a1be800
  [7]: http://www.jianshu.com/p/98bb3bc2b051