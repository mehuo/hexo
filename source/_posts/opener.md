---
 layout: post
 title: "两个页面间的数据交互"
 date: 2017-10-17
 comments: true
 tags: 
    - jquery
    - angular
---

## 普通用法
现在我们有两个页面 a.html 和 b.html，我们将在 a.html 中使用a标签打开 b.html，在b.html中操作后将数据写到a.html上
### a.html
html代码
    
    <a href="b.html target="_blank">在新窗口打开b.html</a><br><br><br>  
    <div id="div_id" style="border:1px solid #F00; width:300px; height:100px; padding:10px">  
        <p>请先点击上面的超链接</p>  
        <p>这里的文字会在你点击<b style="color:#F00">b.html</b>页面中的<b>超链接后</b>改变哦！</p>  
    </div>

js代码

    function b() {  
     var h = document.getElementById("div_2").innerHTML ;  
     window.opener.a(h) ;;  
    }  
  
### b.html
html代码

    <a href="javascript:b()">  
        <div id="div_2">"哈哈！这个<b>数据</b>会发送到<b       style="color:#F00">a.html</b>页面的哦！"</div>  
    </a>
  
js代码

    function b() {  
        var h = document.getElementById("div_2").innerHTML ;  
        window.opener.a(h) ;;  
    }
 
实现效果
a页面打开效果
![image](/images/hexo/jquery/opener-a-1.png)
b页面打开效果
![image](/images/hexo/jquery/opener-b-1.png)
点击b页面链接后a页面的效果
![image](/images/hexo/jquery/opener-a-2.png)


## 在angularJs中用法

### a.html

html代码

    <a href="b.html target="_blank">在新窗口打开b.html</a><br><br><br>  
    <div id="div_id" style="border:1px solid #F00; width:300px; height:100px; padding:10px">  
        <p>请先点击上面的超链接</p>  
        <p>这里的文字会在你点击<b style="color:#F00">b.html</b>页面中的<b>超链接后</b>改变哦！</p>  
    </div>

js代码 需要在controller中引入 $window
  
    var app = angular.module('myApp', []);
    app.controller('aCtrl', function($scope,$window) {
        $scope.a = function(msg){
            alert(msg);
        }
        $window.$scope = $scope;
    });

### b.html代码

html代码

    <a ng-click="b();">  
        <div id="div_2">"哈哈！这个<b>数据</b>会发送到<b       style="color:#F00">a.html</b>页面的哦！"</div>  
    </a>

js代码

    var app = angular.module('myApp', []);
    app.controller('bCtrl', function($scope) {
        $scope.b = function(msg){
            window.opener.$scope.a('你好');
        }
    });




