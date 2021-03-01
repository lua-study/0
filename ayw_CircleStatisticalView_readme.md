**1.控件效果图**

![这里写图片描述](https://img-blog.csdn.net/20180816085941182?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTIxMjc5NjE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**2.知识点**

**（1）图形**
![这里写图片描述](https://img-blog.csdn.net/20180815103339743?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTIxMjc5NjE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
**（2）动画：**

（1）圆饼填充动画

（2）圆点放大动画

（3）折线绘制动画

（3）上部字体延折线移动动画

（4）下部字体从下移动至上动画

以上动画实现都是用ValueAnimator，在ValueAnimator中利用TypeEvaluator中泛型的对象生成从开始到结束的fracation(0-1)的增长数据来生成对应的坐标点或者路劲来进行绘制对应的图形和字体。
```
  public ValueAnimator drawArcAnimation(final int position, final float startAngle, final float sweepAngle) {
        final ValueAnimator valueAnimator = ValueAnimator.ofObject(new TypeEvaluator () {
            @Override
            public Float evaluate(float fraction, Float startValue, Float endValue) {
                return fraction * endValue;
            }
        }, startAngle, sweepAngle);
        valueAnimator.addUpdateListener(new ValueAnimator.AnimatorUpdateListener() {
            @Override
            public void onAnimationUpdate(ValueAnimator animation) {
                statisticalItems.get(position).setSweepAngleAnim((Float) animation.getAnimatedValue());
                invalidate();
            }
        });
        valueAnimator.setDuration(animationDuration);
        valueAnimator.setRepeatCount(0);
        return valueAnimator;
    }
```

**3.使用**

[项目源码下载](https://gitee.com/relin/CircleStatisticalView.git)

[控件类文件下载](http://files.git.oschina.net/group1/M00/04/9C/PaAvDFtziqqAQ9zDAAATxtIiKXE628.zip?token=9b8887a62dbaaed520c8c67c2525d70a&ts=1534300778&attname=%E5%9C%86%E5%BD%A2%E7%BB%9F%E8%AE%A1View.zip)

[控件类文件2.0下载(动画版)](http://files.git.oschina.net/group1/M00/04/9F/PaAvDFt0yrqAUTLnAAAYsqyN4B8530.zip?token=3295fe65777d2da84ac8937ba0eda137&ts=1534381019&attname=%E5%9C%86%E5%9C%88%E7%BB%9F%E8%AE%A1View2.0.zip)

[控件apk下载](http://files.git.oschina.net/group1/M00/04/9C/PaAvDFtzih6ATN4gABSlxVfYKpM948.apk?token=8872d263b5ebeee7f10a8c9dcc28507d&ts=1534300778&attname=%E5%9C%86%E5%BD%A2%E7%BB%9F%E8%AE%A1%E5%9B%BE.apk)

[控件apk 2.0下载((动画版))](http://files.git.oschina.net/group1/M00/04/9F/PaAvDFt0y9uAHJhGABSxQfqy3s8093.apk?token=0ea93955e977914ba584144c36cf75dd&ts=1534381019&attname=%E5%9C%86%E5%9C%88%E7%BB%9F%E8%AE%A1View2.0.apk)

**代码使用：**
```
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        CircleStatisticalView csv = findViewById(R.id.csv);
        //测试数据
        float[] percent = {0.1F, 0.2F, 0.2F, 0.4F, 0.1F};
        int[] color = {Color.parseColor("#FD695D"), Color.parseColor("#FDB57B"), Color.parseColor("#12B166"), Color.parseColor("#1DA0FB"), Color.GREEN};
        String[] markTop = {"13.20", "2.80", "5.74", "24.00", "26.00"};
        String[] markBottom = {"商超", "水房", "其他", "餐饮", "外卖"};

        List  list = new ArrayList<>();
        for (int i = 0; i  
     
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
     
```

(2)CircleStatisticalView

```
import android.animation.AnimatorSet;
import android.animation.TypeEvaluator;
import android.animation.ValueAnimator;
import android.content.Context;
import android.content.res.Resources;
import android.content.res.TypedArray;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.Point;
import android.graphics.RectF;
import android.support.annotation.Nullable;
import android.util.AttributeSet;
import android.util.Log;
import android.view.View;

import java.util.ArrayList;
import java.util.List;

/**
 * Created by Relin
 * on 2018-08-14.
 * 圆形统计图
 */
public class CircleStatisticalView extends View {

    /**
     * 宽度
     */
    private float width;
    /**
     * 高度
     */
    private float height;
    /**
     * 中心坐标
     */
    private float circleX, circleY;
    /**
     * 半径
     */
    private float circleRadius = dpToPx(50);
    /**
     * 圆圈背景颜色
     */
    private int circleBackgroundColor = Color.parseColor("#EDEDED");
    /**
     * 圆圈宽度
     */
    private float circleStrokeWidth = dpToPx(30);

    /**
     * 圆点边距
     */
    private float dotMargin = dpToPx(5);
    /**
     * 圆点半径
     */
    private float dotRadius = dpToPx(5);
    /**
     * 转角线X差值
     */
    private float lineGapX = dpToPx(15);
    /**
     * 转角线Y差值
     */
    private float lineGapY = dpToPx(15);
    /**
     * 标记线上下的文件间距
     */
    private float lineNearTextMargin = dpToPx(5);
    /**
     * 线条粗细
     */
    private float lineStrokeWidth = dpToPx(1.2F);
    /**
     * 标记文字大小
     */
    private float markTextSize = dpToPx(14);
    /**
     * 标记文字颜色
     */
    private int markTextColor = 0;

    /**
     * 数据
     */
    private List  statisticalItems;

    /**
     * 是否使用动画
     */
    private boolean isUseAnimation = true;


    public CircleStatisticalView(Context context) {
        super(context);
        init(context, null);
    }

    public CircleStatisticalView(Context context, @Nullable AttributeSet attrs) {
        super(context, attrs);
        init(context, attrs);
    }

    public CircleStatisticalView(Context context, @Nullable AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
        init(context, attrs);
    }

    @Override
    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        super.onMeasure(widthMeasureSpec, heightMeasureSpec);
        int widthSpecSize = MeasureSpec.getSize(widthMeasureSpec);
        int widthSpecMode = MeasureSpec.getMode(widthMeasureSpec);
        int heightSpecSize = MeasureSpec.getSize(heightMeasureSpec);
        int heightSpecMode = MeasureSpec.getMode(heightMeasureSpec);
        int w = widthSpecSize;
        int h = heightSpecSize;
        int needHeight = (int) (circleRadius * 2 + dotMargin + dotRadius * 2 + circleStrokeWidth * 2 + lineGapY * 4);
        if (widthSpecMode == MeasureSpec.AT_MOST && heightSpecMode == MeasureSpec.AT_MOST) {
            w = (int) (1.7F * needHeight);
            h = needHeight;
        } else if (widthSpecMode == MeasureSpec.AT_MOST) {
            w = 4 * needHeight / 5;
            h = heightSpecSize;
        } else if (heightSpecMode == MeasureSpec.AT_MOST) {
            w = widthSpecSize;
            h = needHeight;
        }
        setMeasuredDimension(w, h);
        //获取最终的宽高
        width = getMeasuredWidth();
        height = getMeasuredHeight();
        circleX = width / 2;
        circleY = height / 2;
        circleRadius -= getPaddingLeft() - getPaddingRight();
    }

    /**
     * 初始化
     *
     * @param context
     * @param attrs
     */
    private void init(Context context, AttributeSet attrs) {
        TypedArray array = context.obtainStyledAttributes(attrs, R.styleable.CircleStatisticalView);
        circleBackgroundColor = array.getColor(R.styleable.CircleStatisticalView_circleBackgroundColor, circleBackgroundColor);
        dotMargin = array.getDimension(R.styleable.CircleStatisticalView_dotMargin, dotMargin);
        dotRadius = array.getDimension(R.styleable.CircleStatisticalView_dotRadius, dotRadius);
        lineGapX = array.getDimension(R.styleable.CircleStatisticalView_lineGapX, lineGapX);
        lineGapY = array.getDimension(R.styleable.CircleStatisticalView_lineGapY, lineGapY);
        lineNearTextMargin = array.getDimension(R.styleable.CircleStatisticalView_lineNearTextMargin, lineNearTextMargin);
        lineStrokeWidth = array.getDimension(R.styleable.CircleStatisticalView_lineStrokeWidth, lineStrokeWidth);
        markTextSize = array.getDimension(R.styleable.CircleStatisticalView_markTextSize, markTextSize);
        markTextColor = array.getColor(R.styleable.CircleStatisticalView_markTextColor, markTextColor);
        statisticalItems = new ArrayList<>();
        array.recycle();
    }

    private int drawCount = 0;

    @Override
    protected void onDraw(final Canvas canvas) {
        super.onDraw(canvas);
        drawCircle(canvas);
        int size = statisticalItems == null ? 0 : statisticalItems.size();
        float startAngle = 0F;
        float markAngle;
        for (int i = 0; i  () {
            @Override
            public Float evaluate(float fraction, Float startValue, Float endValue) {
                return fraction * endValue;
            }
        }, startAngle, sweepAngle);
        valueAnimator.addUpdateListener(new ValueAnimator.AnimatorUpdateListener() {
            @Override
            public void onAnimationUpdate(ValueAnimator animation) {
                statisticalItems.get(position).setSweepAngleAnim((Float) animation.getAnimatedValue());
                invalidate();
            }
        });
        valueAnimator.setDuration(500);
        valueAnimator.setRepeatCount(0);
        return valueAnimator;
    }

    /**
     * 绘制标记和线的动画
     *
     * @param position   位置
     * @param startPoint 开始点
     * @param endPoint   结束点
     * @param step       步骤
     * @return
     */
    public ValueAnimator drawMarkLineAnimation(final int position, final Point startPoint, final Point endPoint, final int step) {
        final ValueAnimator valueAnimator = ValueAnimator.ofObject(new TypeEvaluator () {
            @Override
            public Point evaluate(float fraction, Point startValue, Point endValue) {
                Point point = new Point();
                point.x = (int) (fraction * (endPoint.x - startPoint.x) + startPoint.x);
                point.y = (int) (fraction * (endValue.y - startValue.y) + startPoint.y);
                return point;
            }
        }, startPoint, endPoint);
        valueAnimator.addUpdateListener(new ValueAnimator.AnimatorUpdateListener() {
            @Override
            public void onAnimationUpdate(ValueAnimator animation) {
                switch (step) {
                    case 1:
                        valueAnimator.setDuration(250);
                        statisticalItems.get(position).setGapAnimationPoint((Point) animation.getAnimatedValue());
                        break;
                    case 2:
                        valueAnimator.setDuration(500);
                        statisticalItems.get(position).setLineEndAnimPoint((Point) animation.getAnimatedValue());
                        break;
                    case 3:
                        valueAnimator.setDuration(500);
                        statisticalItems.get(position).setTopMarkAnimPoint((Point) animation.getAnimatedValue());
                        break;
                    case 4:
                        valueAnimator.setDuration(500);
                        statisticalItems.get(position).setBottomMarkAnimPoint((Point) animation.getAnimatedValue());
                        break;
                }
                invalidate();
            }
        });

        valueAnimator.setRepeatCount(0);
        return valueAnimator;
    }


    /**
     * 创建画笔对象
     *
     * @return
     */
    private Paint buildPaint() {
        Paint paint = new Paint();
        paint.setAntiAlias(true);
        paint.setStyle(Paint.Style.STROKE);
        paint.setStrokeWidth(circleStrokeWidth);
        return paint;
    }

    /**
     * 画出背景圆圈
     *
     * @param canvas 画布
     */
    private void drawCircle(Canvas canvas) {
        Paint paint = buildPaint();
        paint.setColor(circleBackgroundColor);
        canvas.drawCircle(circleX, circleY, circleRadius, paint);
    }


    /**
     * 画圆弧
     *
     * @param canvas     画布
     * @param startAngle 开始弧度
     * @param sweepAngle 进过的弧度
     * @param color      弧面颜色
     */
    private void drawArc(Canvas canvas, float startAngle, float sweepAngle, int color) {
        Paint paint = buildPaint();
        paint.setColor(color);
        RectF rectF = new RectF(circleX - circleRadius, circleY - circleRadius, circleX + circleRadius, circleY + circleRadius);
        canvas.drawArc(rectF, -90 + startAngle, sweepAngle, false, paint);
    }

    /**
     * 绘制标记
     *
     * @param canvas    画布
     * @param item      标记数据对象
     * @param markAngle 标记弧度
     */
    private void drawMark(Canvas canvas, int position, StatisticalItem item, float markAngle) {
        final Paint paint = new Paint();
        paint.setAntiAlias(true);
        paint.setStrokeWidth(lineStrokeWidth);
        paint.setColor(item.getColor());
        //圆点
        float dotToCenterLine = circleRadius + dpToPx(20) + dotMargin;
        float dotX;
        float dotY;
        float dotAngle = (float) ((markAngle / 2 * Math.PI / 180));//角度转弧度
        if (markAngle / 2   45 && markAngle / 2   45 && markAngle / 2   45 && markAngle / 2   225 && markAngle / 2   225 && markAngle / 2   getStatisticalItems() {
        return statisticalItems;
    }

    public void setStatisticalItems(List  statisticalItems) {
        int size = statisticalItems == null ? 0 : statisticalItems.size();
        float totalPercent = 0;

        List  newItems = new ArrayList<>();
        for (int i = 0; i < size; i++) {
            if (statisticalItems.get(i).getPercent() != 0) {
                newItems.add(statisticalItems.get(i));
            }
        }
        size = newItems == null ? 0 : newItems.size();
        for (int i = 0; i < size; i++) {
            StatisticalItem item = newItems.get(i);
            totalPercent += item.getPercent();
        }
        if (totalPercent != 1) {
            for (int i = 0; i < size; i++) {
                StatisticalItem item = newItems.get(i);
                newItems.get(i).setPercent(item.getPercent() / totalPercent);
            }
        }
        this.statisticalItems = newItems;

    }

    public boolean isUseAnimation() {
        return isUseAnimation;
    }

    public void setUseAnimation(boolean useAnimation) {
        isUseAnimation = useAnimation;
    }
}


```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)