# Pingpong-mini
毕业设计微信小程序
## :dizzy:**开发指南**

### :runner:开发工具：

##### 1.**微信小程序开发官方文档**

:point_right:https://developers.weixin.qq.com/miniprogram/dev/component/

![image-20210115215831100](C:\Users\transient\AppData\Roaming\Typora\typora-user-images\image-20210115215831100.png)

##### 2.**安装微信开发者工具**

:point_right:https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html

![image-20210115215701509](C:\Users\transient\AppData\Roaming\Typora\typora-user-images\image-20210115215701509.png)

##### 3.**项目结构**

![image-20210115221700186](C:\Users\transient\AppData\Roaming\Typora\typora-user-images\image-20210115221700186.png)

###### 1.**components文件**

​        为了方便代码的后续管理及维护，我们将页面内可重复使用的功能模块抽象成自定义组件，并集中存放在该文件下以便代码复用，降低代码复杂度，节约空间资源，提高性能。Tips：右键选择“创建component”可快速创建四个不同后缀文件。



###### 2.pages文件

​        项目所有页面，若需要在pages下添加新的页面，则只需要在app.json文件中pages下声明文件路径，保存即可。注意：放在最上面的文件路径是最先显示的页面。

```
"pages/signIn/index",            //登录
"pages/signUp/index",            //注册
"pages/commodity/index",         //商品显示（导航栏）
"pages/courseList/index",        //课程显示（导航栏）
"pages/tidings/index",           //客服消息（导航栏）
"pages/venueList/index",         //场馆显示（导航栏）
"pages/personal/index",          //个人中心（导航栏）
"pages/cart/cart",               //购物车（个人中心页触发显示）
"pages/personalInfo/personalInfo",       //个人信息页
"pages/modifyPInfo/modifyPInfo",         //个人信息修改页
"pages/commodityInfo/commodityInfo",     //商品详情页
"pages/conversation/conversation",       //会话页
"pages/courseInfo/courseInfo",           //课程详情页
"pages/venueInfo/venueInfo",     //场馆详情页
"pages/search/search",           //搜索页
"pages/404/404"                  //页面丢失404
```

###### 3.request请求文件

该文件无其他情况无需再改动，只需要调用该文件下的函数加入相应参数即可。

```
export const request = (params) => {
  return new Promise((resolve, reject) => {
      wx.request({
          ...params,
          success:(result)=>{
              resolve(result);
          },
          fail:(err)=>{
              reject(err)
          }
      });
  })
}
```

