# 在express中使用session

1.安装

​    npm i express-session -S

2.导入session模块

  Var session = require('express-session')

3 在express中使用中间件

App.use(session({

secret:'keyboard cat',// 相当于一个加密密钥匙，值可以是任意字符串

reserve: false, // 强制session保存到session store中

saveUnintialized: false// 强制没有初始化的session保存在storage中

}))

只要注册了session中间件，今后只要能访问到req这个对象，必然能访问到req.session

4 将私有数据保存到当前请求的session会话中

// 将登陆的用户保存在session中

req.session.user = result.dataValues

// 设置是否登陆为true

req.session.islogin= true

5 通过destroy()方法清空session数据

```js
req.session.destroy(function(err){
  if(err) throw err
  console.log('login out')
  // 实现服务器端的跳转，
  res.redirect('/')
})
```



# 第三方插件mditor

功能： 1.可以作为一个纯粹的markdown编辑器插件，在前端页面使用

​            2. 在node端，我们可以require（'mditor'）,使用这个模块提供的方法，把markdown解析转换为html内容

# bcrypt加密算法

比md5安全

```js
npm i node-pre-gyp -g
在项目根目录，打开终端，运行cnpm i bcrypt -S
导入模块const bcrypt = require('bcrypt')
定义幂次 const silatRounds =10
调用bcrypt.hash加密
调用bcrypt.compare（）对比密码是否正确  (登陆时做对比使用)
```

