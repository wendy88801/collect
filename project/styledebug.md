
#### 在业务开发过程中，想必大家经常会需要查看一个元素的位置及大小并修改它的 CSS，因此就会频繁使用到 DevTools 中的选择元素功能。

![image](https://mmbiz.qpic.cn/mmbiz_png/tibUxowsg9P0t9AwB0EtUsxc8ice3Hl4QdQUIO8XECJU2fFz2usUtK1tTdtwMINfiafPs3CO9YG3zO4tGMTYB5zsA/640?wx_fmt=png)

###### 其实我们可以使用一个 CSS 技巧给所有元素加上 outline，这样就能迅速了解自己所需的元素位置信息，无须再选择元素查看了。
![image](https://mmbiz.qpic.cn/mmbiz_png/tibUxowsg9P0t9AwB0EtUsxc8ice3Hl4QdKOCULLmzld5hBeDQ3BVQpKhnFe0vlcdiaoaAaFGcI3gjODcgeVibgE3g/640?wx_fmt=png)


<html>
<!--在这里插入内容-->
</html>

###### 我们只需要添加以下 CSS 就能为任何网站添加这样的效果


```
html * {
    outline: 1px solid red
}
```
需要注意的是这里我没有使用 border 的原因是 border 会增加元素的大小但是 outline 不会。

通过这个技巧不仅能帮助我们在开发中迅速了解元素所在的位置，还能帮助我们方便地查看任意网站的布局。

但是当下这个技巧需要我们手动添加 CSS 来实现，显得略微有点鸡肋，是否可以通过一个开关来实现任意网页开启关闭这个功能呢？

答案是有的，我们需要借助 Chrome 的书签功能。

打开书签管理页

右上角三个点「添加新书签」

名称随意，粘贴以下代码到网址中

```
javascript: (function() {
	var elements = document.body.getElementsByTagName('*');
	var items = [];
	for (var i = 0; i < elements.length; i++) {
		if (elements[i].innerHTML.indexOf('html * { outline: 1px solid red }') != -1) {
			items.push(elements[i]);
		}
	}
	if (items.length > 0) {
		for (var i = 0; i < items.length; i++) {
			items[i].innerHTML = '';
		}
	} else {
		document.body.innerHTML +=
			'<style>html * { outline: 1px solid red }</style>';
	}
})();
```
然后我们就可以在任意网站上点击刚才创建的书签，内部会判断是否存在调试的 style。存在的话就删除，不存在的话就添加，通过这种方式我们就能很方便的通过这个技巧查看任意网页的布局了。
