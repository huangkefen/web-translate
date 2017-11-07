## 1 关于
这是一个PDF的浏览器翻译插件，使用国内优秀的翻译软件[iCIBA][1]的即划即译功能。
我做了点小改动，以便在使用浏览器阅读英文PDF文档时更加方便快捷。
也可以浏览普通的英文页面.

## 2 使用说明
1. 安装浏览器脚本插件，[violentmonkey][2](暴力猴) 或者 [greasemonkey][](油猴子) 或者 [tampermonkey][](捣蛋猴)
2. 推荐使用火狐浏览器,因为火狐默认使用[PDF.js](http://mozilla.github.io/pdf.js/)浏览PDF。而chrome需要手动安装,并且由于chrome有较多的安全特性,难以匹配到本地pdf地址。
3. 我用的脚本插件是[violentmonkey][3],主要是因为这个支持firefox的长期支持版,兼容旧版本,而且图标不错,界面简洁.
4. 插件安装之后，新建一个脚本，然后把js文件里的代码全部复制粘贴，保存即可。
5. 可以根据需要做一些改动。比如页面背景色等等都可以很容易在代码中找到。
6. javascript熟悉者也可以自定义添加更丰富的功能。


## 3 url匹配模式简单说明(**重要**)
在js代码的开头有一行注释是:
``` javascript
// @match *://*/* 
```

这个匹配模式是匹配所有url网页.  
也许你并不像这么做,比如你只想匹配本地打开的pdf,则可以改成:  
``` javascript
 // @match file:///*/*.pdf 
```

你还可以额外指定包含和排除模式,比如:
``` javascript
// @include  https://wiki.greasespot.net/*  
// @include  http://mozilla.github.io/pdf.js/web/viewer.html    
// @include /^(http|https)://en\.people\.cn//   
```

+ 模式匹配可参考:[pattern][4] 或者 [match_patterns][]
+ 更详细的文档也可以参考 [tampermonkey-documentation][]

## 4 版本
v1.0  初始版本  
1. 添加了jQuery支持  
2. 即划即译的开关按钮隐藏在pdf页面右上角的菜单中  
3. 支持发音(我在火狐下测试通过,需安装好[flashplayer][5])   
2017/11/06

v1.1  
1. 重构了代码  
2. 代码模块化了,更清晰易懂  
3. 添加对chrome的网页翻译支持(尚未支持本地打开的pdf文件,因为chrome有一些安全机制在阻止外部脚本的执行).  

v1.2  
1.  修复了PDF中的字体重影问题(与PDF.js插件的css冲突的问题)  
2.  在Chrome中使用发音功能的话,需要允许网页执行flash.  

v1.2.1  
修复了chrome下浏览在线pdf时候的字体重影问题.

## 5 Why
初衷是因为Linux下阅读PDF电子文档不方便，也没有一款能让我满意的英文文档阅读工具（对翻译有良好支持）。  
其实其他浏览器也可以使用，比如chrome，但尚未支持PDF，只支持普通的页面，另外还需要更改一下url匹配模式。  


## 6 Chrome兼容问题
+ chrome下的url模式无法匹配chrome-extension开头的地址.(如果有解决方案,请告诉我,感谢!)
## 7 可能存在的问题
+ 发音功能需要安装好flash以及解码器,而部分系统(Linux)或浏览器并未预装





[1]:<http://open.iciba.com/?c=huayi>
[2]:<https://violentmonkey.github.io/get-it/>
[3]:<https://addons.mozilla.org/zh-CN/firefox/addon/violentmonkey/>
[4]:<https://wiki.greasespot.net/Include_and_exclude_rules>
[5]:<http://get.adobe.com/cn/flashplayer>

[greasemonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/greasemonkey/>
[tampermonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/tampermonkey/>
[match_patterns]:<http://code.google.com/chrome/extensions/match_patterns.html>
[tampermonkey-documentation]:<http://code.google.com/chrome/extensions/match_patterns.html>