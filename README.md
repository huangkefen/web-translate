## 1 关于
这是一个双击划词翻译的浏览器脚本插件， 支持PDF和普通网页.  
使用的是国内优秀的翻译软件[iCIBA][1]的即划即译功能。  
我做了点微小的工作，把iCIBA的即划即译功能移植到浏览器上.  
两张效果图如下  
1.  **↓**  firefox下浏览本地pdf :


![view1](https://thumbnail0.baidupcs.com/thumbnail/b3b6e3df3608c5d87bf658488da26635?fid=2013309064-250528-348452523678046&time=1510153200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-Z%2Fy02DdkgWBbAkQAl%2BHB%2BHmGJW8%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=7235231478578735940&dp-callid=0&size=c710_u400&quality=100&vuk=-&ft=video)    


2.  **↓**  chrome下浏览普通网页 :    
![view2](https://thumbnail0.baidupcs.com/thumbnail/00b0173b6d08c2c0673dd7c9e1d3aa71?fid=2013309064-250528-761986531591439&time=1510153200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-Bkr%2BFK8JHPMdgpNcMgZSSh%2BWdNs%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=7235249267459748532&dp-callid=0&size=c710_u400&quality=100&vuk=-&ft=video)  

## 2 使用说明
1. 需要安装浏览器脚本插件，  [violentmonkey][2](暴力猴)   或者 [greasemonkey][](油猴子)   或者 [tampermonkey][](捣蛋猴)
2. 推荐使用火狐浏览器,因为火狐默认使用[PDF.js](http://mozilla.github.io/pdf.js/)浏览PDF。
3. 我用的脚本插件是[violentmonkey][3],主要是因为这个支持firefox的长期支持版,兼容旧版本,而且图标不错,界面简洁.
4. 插件安装之后，新建一个脚本，然后把js文件里的代码全部复制粘贴，保存即可。
6. 修改url匹配模式

## 3 功能特性
1.  双击或划译取词.
2.  支持**本地PDF**的双击划译(目前仅firefox)。
3.  支持**普通网页**的双击划译(firefox和chrome)。
4.  支持PDF页面背景色更改，默认苹果绿，可自定义。
5.  支持**发音**(需安装flash)。
6.  翻译弹窗可固定。
7.  **取词开关**默认隐藏在右上角菜单(PDF模式下)。
8.  跨平台，浏览器+插件。(针对日常使用Linux的朋友)
9.  强大的url正则匹配功能。
10.  持续更新,有时间将会加入其他翻译源的支持.

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
初衷:
- Linux下阅读PDF英文文档不方便，  
- goldendict非常不错,但却不支持foxitpdf的双击取词翻译。  
- youdao dict ,只支持Debian系,浏览英文文档时我感觉也不大好用。  
- 尚未发现一款能让我满意的英文文档阅读工具（Linux下,并且对中文翻译有良好支持）。   
- 自己动手,丰衣足食.  
- 方便自己,方便他人.  

问:为什么在代码中嵌入jquery?  
答:主要是为了避免脚本冲突以及重复加载,避免对原网站造成干扰。


## 6 Chrome兼容问题
+ chrome下无法匹配chrome-extension开头的地址.(如果有解决方案,请告诉我,感谢!)
+ chrome下无法发音.经我初步排查,疑是官方脚本中的mp3发音代码对chrome的兼容问题.我目前还没什么有效的解决方案.

## 7 尚未支持的少数网页
+ github.io上的某些页面,如[sarabander][]无法成功查询到数据.可能是默认脚本安全机制的问题.
+ 爱词霸官方API接口目前存在一些问题.并且因为我对前端不是很熟悉(主后端开发和算法),若有好的修正方案,可留言告知,感激不尽.


[1]:<http://open.iciba.com/?c=huayi>
[2]:<https://violentmonkey.github.io/get-it/>
[3]:<https://addons.mozilla.org/zh-CN/firefox/addon/violentmonkey/>
[4]:<https://wiki.greasespot.net/Include_and_exclude_rules>
[5]:<http://get.adobe.com/cn/flashplayer>

[greasemonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/greasemonkey/>
[tampermonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/tampermonkey/>
[match_patterns]:<http://code.google.com/chrome/extensions/match_patterns.html>
[tampermonkey-documentation]:<http://code.google.com/chrome/extensions/match_patterns.html>
[sarabander]:<https://sarabander.github.io/sicp/html/index.xhtml>
