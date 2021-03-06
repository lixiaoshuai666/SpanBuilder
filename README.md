# SpanBuilder
## <font color="red"> 一个TextView可设置如下的效果</font>
# 使用说明：

##导入
### Android studio 
```
compile 'com.zrq:spanbuilder:1.0.2'
  
```
### Eclipse
```
导入app/libs/spanbuilder-1.0.2.jar
  
```

##常用效果：
![image](https://github.com/zrq1060/SpanBuilderDemo/blob/master/screenshots/0.png)
```
SpannableStringBuilder spannableStringBuilder = new SpannableStringBuilder();
spannableStringBuilder
        .append(new SpanBuilder("8").setTextSize(45).setTextColor(Color.RED))
        .append(new SpanBuilder(".88").setTextSize(28).setTextColor(Color.RED))
        .append(new SpanBuilder("%\n").setTextSize(16).setTextColor(Color.BLACK));

spannableStringBuilder
        .append(new SpanBuilder("10").setTextSize(50).setTextColor(Color.RED).setTypeface(Typeface.BOLD_ITALIC))
        .append(new SpanBuilder("元\n").setTextSize(16).setTextColor(Color.BLACK));

spannableStringBuilder
        .append(new SpanBuilder("￥149").setTextSize(24).setTextColor(Color.RED))
        .append(new SpanBuilder(".9  ").setTextSize(16).setTextColor(Color.RED))
        .append(new SpanBuilder("￥259.00").setTextSize(20).setTextColor(Color.BLACK).setDeleteLine())
        .append(new SpanBuilder("   4738").setTextSize(20).setTextColor(Color.RED))
        .append(new SpanBuilder("件已售\n").setTextSize(20).setTextColor(Color.BLACK));

textView.setText(spannableStringBuilder);

```
##用法 1之单一样式：

![image](https://github.com/zrq1060/SpanBuilderDemo/blob/master/screenshots/1.png)
```
SpannableStringBuilder spannableStringBuilder = new SpannableStringBuilder()
        .append(new SpanBuilder("\n！！此页面看的的所有内容就是一个TextView\n\n").setBackgroundColor(Color.RED))
        .append(new SpanBuilder("字体30Sp").setTextSize(30))
        .append(new SpanBuilder("字体红色").setTextColor(Color.RED))
        .append(new SpanBuilder("字体背景绿色").setBackgroundColor(Color.GREEN))
        .append(new SpanBuilder("粗斜体").setTypeface(Typeface.BOLD_ITALIC))
        .append(new SpanBuilder("自定义Style样式").
                setTextAppearance(getApplicationContext(), android.R.style.TextAppearance_Small))
        .append(new SpanBuilder("可点击").setClick(textView, new ClickableSpan() {
            @Override
            public void onClick(View widget) {
                // ！！点击了内容，但是会触发TextView的点击事件
                Toast.makeText(getApplicationContext(), "ClickSpan点击了", Toast.LENGTH_LONG).show();
            }
        }))
        .append(new SpanBuilder("删除线").setDeleteLine())
        .append(new SpanBuilder("下划线").setUnderLine())
        .append(new SpanBuilder("此内容无效，会被图片给替换").setImage(drawable))
        .append(new SpanBuilder("字体类型为monospace\n").setFontFamily("monospace"))
        .append(new SpanBuilder("设置蓝色的引用线\n").setQuote(Color.BLUE))
        .append(new SpanBuilder("设置此内容的对齐方式为相反\n").setAlignment(Layout.Alignment.ALIGN_OPPOSITE))
        .append("设置字体大小为之前的")
        .append(new SpanBuilder("2倍\n").setRelativeSize(2.0f))
        .append("这是")
        .append(new SpanBuilder("上标").setUpLabel())
        .append("这是")
        .append(new SpanBuilder("下标\n").setUnderLabel())
        .append(new SpanBuilder("X轴缩放3倍\n\n").setScaleX(3f));

textView.setText(spannableStringBuilder);

```
##用法 2之混合样式：

![image](https://github.com/zrq1060/SpanBuilderDemo/blob/master/screenshots/2.png)
```
SpanBuilder spanBuilder = new SpanBuilder("此为混合样式应用于部分,设置字体15sp、红色、背景绿色、粗斜体")
        .setTextSize(15)
        .setTextColor(Color.RED)
        .setBackgroundColor(Color.GREEN)
        .setTypeface(Typeface.BOLD_ITALIC);

textView.setText(new SpannableStringBuilder().append("开始").append(spanBuilder).append("结束\n\n"));

```
##用法 3之给混合样式部分内容添加（或替换）新样式：

![image](https://github.com/zrq1060/SpanBuilderDemo/blob/master/screenshots/3.png)
```
SpanBuilder oldSpan = new SpanBuilder("给混合样式部分内容添加（或替换）新样式,设置其为蓝色、背景红色")
        .setTextSize(15)
        .setTextColor(Color.RED)
        .setBackgroundColor(Color.GREEN)
        .setTypeface(Typeface.BOLD_ITALIC);

// 新样式的容器
SpanBuilder newSpanStyle = new SpanBuilder()
        .setTextColor(Color.BLUE)
        .setBackgroundColor(Color.RED);
// newSpanStyle里面的样式会添加（或替换）原来oldSpan的样式
oldSpan.addNewSpanStyle(5, 16, newSpanStyle);

textView.setText(new SpannableStringBuilder().append("开始").append(oldSpan).append("结束\n\n"));
```
##用法 4之扩展：添加自定义样式
```
// 4.1 作用于所有
new SpanBuilder("X轴缩放3倍\n").setSpanAll(
        new ForegroundColorSpan(Color.RED),//字体红色
        new BackgroundColorSpan(Color.GREEN), //删除线
        new ScaleXSpan(2.5f));
// 4.1 作用于部分
new SpanBuilder("X轴缩放3倍\n").setSpanPart(1, 5,
        new ForegroundColorSpan(Color.RED),//字体红色
        new BackgroundColorSpan(Color.GREEN), //删除线
        new ScaleXSpan(2.5f));
                
```

#####联系我：

QQ：273902141

邮箱：zrq1060@163.com


        
