## 1 关于
+ 双击划词翻译,浏览器脚本插件，支持PDF和普通网页. 
+ 使用国内优秀翻译软件[iCIBA][1]的即划即译功能。
+ 最近更新(2018/06/12):添加右键打开本地PDF的功能，支持Chrome和Firefox，自动加载取词脚本

+ **firefox扩展: [Web-Translate-firefox][]**
+ **chrome扩展: [Web-Translate-chrome][]**
 

## 2 功能特性
1. 双击或划译取词.
2. 支持**本地PDF**的双击划译。
3. 可用右键**打开本地PDF**并自动加载取词插件。
4. 支持**普通网页**的双击划译,翻译弹窗可固定。
5. 支持**自定义任意页面的css样式**,比如PDF页面背景色更改，默认苹果绿。
6. 支持**发音**(firefox和chrome)。
7. 简洁但强大的配置页面。
8. 右键动态加载取词脚本。
9. 强大的url正则匹配功能。
10. **持续迭代更新**
11. 跨平台，浏览器+扩展。(针对日常使用Linux的朋友)。

## 3 扩展使用说明  

1. 安装[Web-Translate-firefox][] 或 [Web-Translate-chrome][]
2. 右键可进入配置页面,也可动态加载取词脚本
3. 配置页面中添加url规则,用空格分开规则和注释(可为空),点击保存即可.格式为 **规则+空格+注释**,例子如下
4. 例如"*://*.github.com/* 匹配所有github.com页面" (去掉双引号)
5. 使用换行符分开多条规则.
6. 如果你删除了所有规则,再点击一次"保存"按钮,就会出现"恢复默认"按钮,可恢复默认配置.
7. PDF模式和WEB模式的配置,留空白并点击保存按钮将恢复默认.  

## 4 URL匹配规则(**重要**)

参考 [match_patterns_360][] 或 [match_patterns_Mozilla][] 或 [match_patterns_Google][]
 

## 5 JS版本使用说明

1. 安装浏览器插件，[violentmonkey][2](暴力猴) 或者 [greasemonkey][](油猴子) 或者 [tampermonkey][](捣蛋猴)
2. 推荐[火狐][6],因为火狐默认使用[PDF.js](http://mozilla.github.io/pdf.js/)加载本地PDF。
3. 推荐插件[violentmonkey][3],向下兼容,图标好看,界面简洁.
4. 插件安装后，新建脚本，然后把js文件里的代码全部粘贴进去，保存。
5. 按需修改url匹配模式,即可正常使用.
6. **建议安装firefox和chrome扩展使用**

在js代码的开头有一行注释是:
``` javascript
// @match *://*/* 
```
以上这个匹配模式是匹配所有url网页.  
也许你并不像这么做,比如你只想匹配本地打开的pdf,则可以改成:  
``` javascript
 // @match file:///*/*.pdf 
```

你还可以额外指定包含和排除模式,比如:
``` javascript
// @include  https://wiki.greasespot.net/*  
// @include  http://mozilla.github.io/pdf.js/web/viewer.html    
// @include /^(http|https)://en\.people\.cn//   
// @exclude  https://github.com/*
```

+ js版的模式匹配可参考:[include_and_exclude_rules][4] 或者  [tampermonkey-documentation][]
+ chrome下不支持**本地pdf**,因为无法匹配chrome-extension开头的地址.(chrome目前不允许匹配插件地址)
+ chrome下发音的问题已于2017/11/14通过修改发音代码解决,现可完美发音,无需flash支持,请更新脚本代码.
+ [sarabander][]  该网页存在较严格的代码审查,iciba官方的一些代码无法通过校验,因此在该网页上无法正常加载.
+ [github.com][]  未经github签名的脚本会被拒绝注入,并且安全策略不允许跨域访问,因此也无法正常加载.
+ 后续有时间会写成firefox和chrome的扩展,这样就可以解决以上这些棘手的问题了.

## 6 Why
初衷:
- Linux下阅读PDF英文文档不方便，  
- goldendict非常不错,但却不支持foxitpdf的双击取词翻译。  
- youdao dict ,只支持Debian系,浏览英文文档时我感觉也不大好用。  
- 尚未发现一款能让我满意的英文文档阅读工具（Linux下,并且对中文翻译有良好支持）。   
- 自己动手,丰衣足食.  
- 方便自己,方便他人.  

问:js版为什么在代码中嵌入jquery?  
答:主要是为了避免脚本冲突以及重复加载,避免对原网站造成干扰。


## 7 截图效果

**↓↓↓**  在firefox下浏览本地pdf 以及 在chrome下浏览普通网页  **↓↓↓**   

![view1](http://oz6vony8d.bkt.clouddn.com/pdf-translate-view1.jpg)      
-----------------------------
![view2](http://oz6vony8d.bkt.clouddn.com/pdf-translate-view2.jpg)  

[1]:<http://open.iciba.com/?c=huayi>
[2]:<https://violentmonkey.github.io/get-it/>
[3]:<https://addons.mozilla.org/zh-CN/firefox/addon/violentmonkey/>
[4]:<https://wiki.greasespot.net/Include_and_exclude_rules>
[5]:<http://get.adobe.com/cn/flashplayer>
[6]:<https://www.mozilla.org/zh-CN/firefox/new/>
[greasemonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/greasemonkey/>
[tampermonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/tampermonkey/>
[tampermonkey-documentation]:<http://tampermonkey.net/documentation.php>
[sarabander]:<https://sarabander.github.io/sicp/html/index.xhtml>
[github.com]:<https://github.com>
[Web-Translate-firefox]:<https://addons.mozilla.org/addon/web-translate?src=external-github>
[Web-Translate-chrome]:<https://chrome.google.com/webstore/detail/web-translate/hcgieffgpbjghiibedcileaobhopaodg?hl=zh-CN>

[match_patterns_Google]:<http://code.google.com/chrome/extensions/match_patterns.html>
[match_patterns_Mozilla]:<https://developer.mozilla.org/zh-CN/Add-ons/WebExtensions/Match_patterns>
[match_patterns_360]:<http://open.chrome.360.cn/extension_dev/match_patterns.html>
