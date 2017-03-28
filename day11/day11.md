# day11

标签（空格分隔）： 每日计划

---
##时间--2017年3月16号

###空余时间

 [解决ScrollView下嵌套ListView／GridView进页面不在顶部的问题以及数据显示不全的问题（ 只显示一行）][1]

###公司项目

社区详情页Model搭建(自己搭建,后台还没有接口),查看需求,要图

###每日GET技能

```
	/**
	 * 禁止ScrollView内布局变化后自动滚动
	 */
	@Override
	protected int computeScrollDeltaToGetChildRectOnScreen(Rect rect) {
		return 0;
	}
```
  [1]: http://blog.csdn.net/yy1300326388/article/details/47107089