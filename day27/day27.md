# day27

标签（空格分隔）： 每日计划

---
##时间--2017年4月1号

###空余时间
*  [如何取得View的位置之View.getLocationInWindow()的小秘密][1]
*  

###公司项目



###每日GET技能

```

 /**
     * 定位到评论区
     */
    private void goCommentLocation() {

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                //如果recyclerview和scrollview都不为空的时候进行判断recyclerview的所在的位置
                if(lv_comment != null && scro_observer != null) {
                    int[] comment_numxy = new int[2];
                    int[] easyScrollxy = new int[2];
                    lv_comment.getLocationInWindow(comment_numxy);
                    scro_observer.getLocationInWindow(easyScrollxy);
                    scro_observer.smoothScrollTo(0, comment_numxy[1] - easyScrollxy[1]);
                }
            }
        },1000);
    }
```

  [1]: http://blog.csdn.net/imyfriend/article/details/8564781
