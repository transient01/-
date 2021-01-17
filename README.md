# Pingpong-mini
毕业设计微信小程序
## ## :dizzy:**开发指南**

### :runner:开发工具：

##### 1.**微信小程序开发官方文档**

:point_right:https://developers.weixin.qq.com/miniprogram/dev/component/

![image-20210115215831100](C:\Users\transient\AppData\Roaming\Typora\typora-user-images\image-20210115215831100.png)

##### 2.**安装微信开发者工具**

:point_right:https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html

![image-20210115215701509](C:\Users\transient\AppData\Roaming\Typora\typora-user-images\image-20210115215701509.png)

## :link:开发流程

##### :white_medium_square:1.克隆项目

```
git clone https://github.com/transient01/Pingpong-mini.git  # 注意拉取 master 分支代码
```

:white_medium_square:  2. **创建分支**

```bash
git checkout -b '新的分支名'  # 新建分支并切换到新的分支

git branch # 查看分支 
```

:white_medium_square:  3. **编写代码 (详见模块功能)** 


:white_medium_square:  4. **保存代码**

```bash
git add . # 保存代码到本地 git 仓库
```

:white_medium_square: 5.  **合并代码**

```bash
# 提交前注意拉取远程 master 分支代码，避免发生合并冲突

git remote # 查看远程主机名 (origin)

git checkout master # 切换回 master 分支，切换前记得保存代码！

git pull origin master # <远程主机名> <远程分支名>:<本地分支名>  如果远程分支是与当前分支合并，则冒号后面的部分可以省略

# 以上命令表示，取回 origin/master 分支再与本地 master 合并，等同于 git fetch origin，然后 git merge origin/master
```

:white_medium_square: 6.  **提交代码**

```bash
git checkout '你的分支名' # 切换回你的分支

git merge master # 合并 master 并解决代码合并冲突

git commit -m"简单描述你的代码功能"
```

:white_medium_square: 7. **推送远程**

```bash
# 先在 github 上创建你的新分支

git push origin '你的分支名' # 把本地分支推送到远程分支

# 然后在 github 上提交 Merge pull request ，把你的分支代码合并到远程 master，具体操作步骤可参考以下官方文档
```

## :penguin:目录结构

```js
Pingpong-mini
├─app.js                                                #全局对象文件程序入口
├─app.json                                              #全局配置文件
├─app.wxss                                              #全局样式文件
├─project.config.json                                   #发布及兼容配置
├─sitemap.json                                          #是否可被微信索引配置文件
├─utils                                                 #方法库
|   └util.js
├─style                                                 #样式文件
├─request                                               #接口请求文件
|    └index.js
├─pages                                                 #小程序页面文件
|   ├─venueList                                         #场馆显示（导航栏）
|   |     ├─index.js                                    #页面入口函数文件
|   |     ├─index.json                                  #页面配置文件
|   |     ├─index.wxml                                  #页面布局文件
|   |     └index.wxss                                   #页面样式文件
|   ├─tidings                                           #客服消息（导航栏）
|   |    ├─index.js
|   |    ├─index.json
|   |    ├─index.wxml
|   |    └index.wxss
|   ├─signUp                                            #注册
|   |   ├─index.js
|   |   ├─index.json
|   |   ├─index.wxml
|   |   └index.wxss
|   ├─signIn                                            #登录
|   |   ├─index.js
|   |   ├─index.json
|   |   ├─index.wxml
|   |   └index.wxss
|   ├─search                                            #搜索页
|   |   ├─search.js
|   |   ├─search.json
|   |   ├─search.wxml
|   |   └search.wxss
|   ├─personal                                          #个人中心（导航栏）
|   |    ├─index.js
|   |    ├─index.json
|   |    ├─index.wxml
|   |    └index.wxss
|   ├─courseList                                        #课程显示（导航栏）
|   |     ├─index.js
|   |     ├─index.json
|   |     ├─index.wxml
|   |     └index.wxss
|   ├─commodity                                         #商品显示（导航栏）
|   |     ├─index.js
|   |     ├─index.json
|   |     ├─index.wxml
|   |     └index.wxss
|   ├─404                                               #页面丢失404
|   |  ├─404.js
|   |  ├─404.json
|   |  ├─404.wxml
|   |  └404.wxss
├─icons                                                 #图标文件
├─components                                            #公共组件文件
|     ├─searchInput                                     #组件样例文件
|     |      ├─searchInput.js
|     |      ├─searchInput.json
|     |      ├─searchInput.wxml
|     |      └searchInput.wxss
```

###### 1.**components文件**

​        为了方便代码的后续管理及维护，我们将页面内可重复使用的功能模块抽象成自定义组件，并集中存放在该文件下以便代码复用，降低代码复杂度，节约空间资源，提高性能。Tips：右键选择“创建component”可快速创建四个不同后缀文件。

###### 2.pages文件

​        项目所有页面，若需要在pages下添加新的页面，则只需要在app.json文件中pages下声明文件路径，保存即可。注意：放在最上面的文件路径是最先显示的页面。

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

## :rabbit2:模块功能

![乒乓球毕设-mini](C:\Users\transient\Desktop\毕设\乒乓球毕设-mini.png)

## :whale2:详细代码分析（待更）
