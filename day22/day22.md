# day22

标签（空格分隔）： 每日计划

---
##时间--2017年3月28号
[Android中Recyclerview监听是否滑动到底部][1]
###空余时间
[年近30，我的职业回顾与思考][2]
###公司项目
三级评论优化 详情界面逻辑优化(点赞,收藏,关注,删除动态)
###每日GET技能

####解决当ScrollView嵌套ListView/RecyclerView的时候,监听ListView/或者RecyclerView的滑动到底部不响应事件
```
public class ObservableScrollView extends ScrollView {

    private int flag = 0;    //并发控制标志位

    private OnScrollViewDownListener onScrollViewDownListener;


    private ScrollViewListener scrollViewListener = null;

    View.OnTouchListener mGestureListener;
    private GestureDetector mGestureDetector;


    public ObservableScrollView(Context context) {
        super(context);
    }

    public ObservableScrollView(Context context, AttributeSet attrs,
                                int defStyle) {
        super(context, attrs,defStyle);
    }

    //listview  recyclerview 加载完毕，将并发控制符置为0
    public void loadingComponent() {
        flag = 0;
    }

    public ObservableScrollView(Context context, AttributeSet attrs) {
        super(context, attrs);
    }

    public void setScrollViewListener(ScrollViewListener scrollViewListener) {
        this.scrollViewListener = scrollViewListener;

    }

    @Override
    protected void onScrollChanged(int x, int y, int oldx, int oldy) {
        super.onScrollChanged(x, y, oldx, oldy);

        View view = this.getChildAt(0);
        //如果scrollview滑动到底部并且并发控制符为0，回调接口向服务器端请求数据
        if (this.getHeight() + this.getScrollY() == view.getHeight() && flag == 0) {
            flag = 1;//一进来就将并发控制符置为1，虽然onScrollChanged执行多次，但是由于并发控制符的值为1，不满足条件就不会执行到这
            onScrollViewDownListener.DownScrollViewListener();
        }

        if (scrollViewListener != null) {
            scrollViewListener.onScrollChanged(this, x, y, oldx, oldy);
        }
    }

    public void setOnScrollViewDownListener(OnScrollViewDownListener onScrollViewDownListener) {
        this.onScrollViewDownListener = onScrollViewDownListener;
    }

    /**
     * 解决当ScrollView嵌套ListView/RecyclerView的时候,监听ListView/或者RecyclerView的滑动到底部不响应事件
     */
    public interface OnScrollViewDownListener {
        public void DownScrollViewListener();
    }

}

```


  [1]: http://www.loongwind.com/archives/189.html
  [2]: https://mp.weixin.qq.com/s?__biz=MzI2OTQxMTM4OQ==&mid=2247484698&idx=1&sn=d16d134f9c840adbfeb34c97b54cd93b&chksm=eae1f048dd96795eabf2be7f6fbf3a0ae7648dd3b3fccdc638123a6d376d9991cdb51847a0cc#rd