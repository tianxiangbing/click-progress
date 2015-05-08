# click-progress
点击的进度条
例子见[DEMO](http://www.lovewebgames.com/jsmodule/click-progress.html)  
![预览效果:](http://www.lovewebgames.com/jsmodule/images/ui/click-progress.png "点击预览效果")
#使用方法案例:
    <div class="progress"><div class="progress-finished"></div></div>
    <input type="button" value="click" id="click"/>
    $('#click').ClickProgress({
        target:$('.progress'),
        v:5,
        a:1,
        change:'height',//width时是横向，可以看demo
        time:30,
        clicked:function(a,b,c){
            console.log(c,'加油')
            },
        progress:function(a,b,c){
            console.log(c)
            },
        callback:function(){
            alert('完成了')
        }
    });
#或者requirejs
    requirejs.config({
        //By default load any module IDs from js/lib
        baseUrl: '../src',
        paths: {
            $: 'zepto'
        }
    });
    require(['click-progress','$'], function(ClickProgress,$) {
        var cp = new ClickProgress();
        cp.init({
            trigger:$('#click'),
            target:$('.progress'),
            v:5,
            a:1,
            change:'height',
            time:30,
            clicked:function(a,b,c){
                console.log(c,'加油')
                },
            progress:function(a,b,c){
                console.log(c)
                },
            callback:function(){
                alert('完成了')
            }
        });
     });
#属性和方法
##trigger:
    触发事件的对象
##target:
    进度条对象dom，结果有两层
##v:
    每次点击的初始速度
##a:
    加速度，可以理解为重力或摩擦力
##change:height/width
    是改变的高度还是width,默认为height
##time:
    频率
##clicked:function(a,b,c)
    点击后的回调，a是trigger,b是target,c是当前的power值，下面的一样
##progress:function(a,b,c)
    每次进度改变的回调
##callback:function(a,b,c)
    结束后的回调，这里指达到100%;