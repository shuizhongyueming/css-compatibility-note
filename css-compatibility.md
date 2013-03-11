1. 在IE6中，a标签的hover，要想使其有效，应该加上href属性并写入一个值

2. 在一个块级元素内部有两个行级元素，如果其中一个浮动，则两个行级元素无法保持在同一行，为了能够，则另一个行级元素也应该浮动

3. 块级元素浮动之后在加边距，在IE6下面就会有双倍的边距，这个时候针对这个块级元素添加一个display:inline就可以

4. 两个块级元素相邻，并且浮动的时候，如果宽度，高度为设置的话，可能会挤在一起，因根据需要添加

5. 在IE6下，当背景图片高度很小（小于18px）的时候，背景图片下面会有空白，因为IE6里面默认了div的最小高度为18，当低于这个值的时候，会自动的把高度增加到18px。可以通过overflow:hidden;解决这个问题

6. 当一个块级元素内部有浮动的时候,为了能够包含该浮动,需要给该块级元素添加一个overflow:hidden;但是这个在IE6中似乎还必须将该块级元素的高度，宽度等设定好

7. IE6中图片下面有空白，一般可以通过给图片添加display:block;解决此问题

8. 关于有position:absolute;样式的标签，在IE6里面似乎不可以定位到position:fixed;的标签上，因为IE6不支持position:fixed;

9. 在Firefox和chrome里面,当一个元素有背景的时候,如果它的子元素有margin,则margin产生的效果作用在父元素而非子元素上,可以通过在父元素上添加overflow:hidden;解决

10. 操蛋的，在IE中，<option>标签不支持display:hidden;这个没有什么解决方案，只能remove和add去控制他们的隐藏和显示

11.在IE6,7中，float:right;换行的bug （类似于bug2）
     <div>
          <span>normal</span>
          <span style="float:right">float right</span>
     </div>
在上面的例子中，第二个span最后会在第一个span的下一行显示
解决方案：
给div加上zoom:1;overflow:hidden;触发layout和BFC(Block Formatting Context)，防止内部浮动影响外围
给第一个span加上float:left;或者把第二个span放到第一个前面

12.li里面放置了很多的块级元素，在IE下，li的上部或者下部会莫名其妙的多出一到两个像素，为了解决这个问题，可以给li添加一个vertical-align:middle;

13.这个是ie67的一个bug, 当某块级元素设置了 margin-top ，并且之前存在着可被渲染的绝对定位元素时，其 margin-top 在 IE6 IE7会失效。解决方式，把该绝对定位的元素放在需要margin-top的元素的后面，或者该用padding-top

14.如果DIV中没有文字, 鼠标移过div不会有手型出现(FF中没有问题), 经测试发现如果有background-color可以解决这个问题, 所以如果再加一个完全透明就可以解决问题 background-color:white;opacity:0;filter:alpha(opacity=0)

15.input type="text"的边框如果想去除的话应该是用border: medium none;因为在IE下，直接使用border:none;是无法隐藏边框的。其他的元素的边框似乎都可以通过border:none;去除

16.当字体的大小大于22PX左右的时候，可以考虑不用加粗，因为这个时候已经字体的粗细已经足够了

17.有时候对一个DIV进行margin-top的时候的值为负值时，在Firefox下会出现奇怪的偏差，大概在10px左右，为了解决这个问题，可以给该DIV加一个overflow: hidden;就能解决

18.在非IE的浏览器中，当input type="text"的输入框为选中状态时，在框四周会有一个轮廓线，如果想去除的话，可以考虑使用outline属性，当然也可以通过这个属性去修改轮廓线的样式

19.IE6的奇数BUG，在IE6里面有很多地方会出现一些奇怪的奇数bug，有的要求是奇数，有的要求不能为奇数，否则会产生1px的差距。但凡遇到此类的问题时，可以考虑是不是此类问题。像我遇到的一个问题就是父元素高度auto，有个padding-bottom: 3px;子元素相对其绝对定位，bottom: -1px;可是在IE6里面，总是显示为bottom:0px;(猜测的，因为设置-1px是为了遮住父元素的border，而IE6里面没有遮住），后来把padding-bottom: 3px改为4px，然后就正常显示了，不用hack

20.在IE6下，父元素position: static;子元素position: relative;可能会发生一些偏移或者串位的现象，可以尝试着给父元素设置为： position: relative;解决此问题

21.IE6中元素height设定，若line-height的值大于height值，会使得元素的高度增加

22.IE6下在html中使用注释的时候要注意，尽量不要再浮动元素附近使用，可能会影响到排版

23.IE6下对透明图片使用滤镜之后，该透明图片无法使用background-position

24.IE浏览器里面如果在input type="text"中输入了内容，然后按F5刷新的时候，浏览器似乎会保存你上一次输入的内容，这一个细节要注意

25.在IE6下面，比较两个元素的层级，比较的不单单是它们本身的，还有它们父元素所在的层级

26.display:block;的li,竖向排列多个，在IE和非IE浏览器下面，高度会有几个像素的差距。给li加上vertical-align: middle;一般能够解决这些高度的偏差————求解释为什么

27.绝对定位的a标签在IE下面   元素无内容 || 元素无背景（没有背景图和背景色）    会无法点击
解决办法：（1）给元素加透明的背景图，做个1*1px的透明图片 （2） background-color:white;opacity:0;filter:alpha(opacity=0) 参考条例14
（3）background:url(about:blank) || background: url(#) 
第三种方法平时用用是可以的，但是在某种情况下会有bug, 比如JS拖动层时候，拖动的事件在一个透明层上面，你有设置了其他鼠标光标，这时候拖动就会出现光标闪烁的现象！

28. IE6对ul中和li同级的块级元素的解析错误
在IE6里面以下结构

     <ul>
          <li></li>
          <div></div>
          <li></li>
          <div></div>
     </ul>
     
会被解析成如下情况

     <ul>
          <li><div></div></li>
          <li><div></div></li>
     </ul>


29. webkit password 的一个奇怪问题，这个在一般的浏览器如Chrome中不存在，但是在webview和Android原生的浏览器中存在
如下的结构：

     <div class="fm-input J-text-input"><label for="J-fmPwd">密啊啊啊啊啊啊啊啊码：</label><input type="password" placeholder="输入密码" id="J-fmPwd" name="password"></div>

     div{position: relative;}
     label{position: absolute;background: #FCC;}

label通过绝对定位放置在input上面。
当password获取焦点的时候，label的背景色消失，同时label中的文本变成password的placeholder（仅是效果上如此，通过js输出password的placeholder的值还是没变的）

解决方式，把input type="password" 变成 input type="text" 同时给input添加样式-webkit-text-security: disc;这样就能使用text模拟出password的效果，同时不会产生该bug

30. 在webview和Android原生浏览器里面，input(text) input(password) 在获取焦点的时候，似乎会把对应label的值以类似placeholder的方式填充到input框里面。暂时不知道如何使用css解决此问题。用js的方式就是把label标签改成span，防止获取焦点时的问题，同时给span绑定点击事件，点击时使得对应input focus
