
    解决ios fixed定位导致input失去焦点的时候看不到fixed元素代码
   
    let input = [...document.getElementsByTagName('input')]
    input.forEach(ele => {
      ele.onblur = () => {
        setTimeout(() => {
          window.scrollTo(0, 0)
        }, 100)
      }
    })

 
## [ios系统针对底部input设置fixed的输入框不兼容问题](https://blog.csdn.net/qq_32601115/article/details/53158430?_blank) ##


### 11.4 todoList
 [x]　试着发布成功一个npm 包的流程
 []  了解 package.json   所以的配置参数
 []  搭建一个私有npm  
