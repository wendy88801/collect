### 关于css的解决方案
、、、
1. overflow:hidden;

这是最多人开始想到的解决方法，虽然在pc端可以解决问题，但在移动端是不行的，
但有人说在html,body同时设置overflow:hidden可以，但经测试，效果不啥的。。。
在安卓上勉强还行，但会有一卡一卡的效果，ios上直接不行

、、、
// vue
watch:{
    showMark:function(val){
        if(val){
            document.body.style.overflow = 'hidden';
            document.documentElement.style.overflow = 'hidden';
        }else{
            document.body.style.overflow = 'auto';
            document.documentElement.style.overflow = 'auto';
        }
    }
}

### 关于js的解决方案

、、、
// vue下，直接加一个@touchmove.prevent

// 用原生js,则统一给一个class元素添加touchmove事件，并阻止默认行为
// 这里使用了jquery
$('.stop-scroll').on('touchmove',function(e){
    e.preventDefault();
})


