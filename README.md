upload组件
======
upload组件支持IE10以上及firefox，chrome浏览器
*功能： 1丶可自选支持多图片上传
        2丶可限制每张图片大小
具体操作如下：
--------
####1丶首先将index.js添加至html页面中
![](https://github.com/lidingkorol/js-upload-/raw/master/photo/QQ图片20160731112807.png) 
####2丶然后在html页面中添加如下模块
![](https://github.com/lidingkorol/js-upload-/raw/master/photo/QQ图片20160731113100.png)
####3丶最后在html页面设置相关参数
![](https://github.com/lidingkorol/js-upload-/raw/master/photo/QQ图片20160731113226.png)
####4丶参数设置见index.js
![](https://github.com/lidingkorol/js-upload-/raw/master/photo/QQ图片20160731113257.png)
####5丶服务器返回的数据代码编写
        1丶如果是IE9以下，请在index.js的 handleData（）{
                if(document.all && !window.atob)
		{	
		        此处编写返回操作，数据储存在<iframe id="sendIframe" name="sendIframe"><iframe>中
		}	
        }
        2丶如果是IE10以上及其他浏览器，请在index.js的handleData(){
                else
		{
			此处编写返回操作，服务器返回数据储存在<div id="output"></div>中，this.output.innerHTML可取到完整数据
			
		}
        }
#以上是readme所有内容

#总体思路正确
优化点：
1：iframe+form不需要用户自己写，用JS自动生成
2：不要让用户改你的JS代码，一旦JS模块化，用户是没有权限改JS插件代码的
建议：
upload初始化的几个参数的建议
```html
<script>
var upload=new Upload({
	target:'element',
	accept:'img',
	multiple:true,
	url:'url',
	success:function(){},
	error:function(){}
})
</script>
```
最后
关于IE9不支持的问题，用iframe+form组合来上传文件，至于本地无法设置domain的问题，先把这个功能完善，做好了我放我公司服务器跑一遍。
