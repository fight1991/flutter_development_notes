# flutter_development_notes
flutter开发笔记
## 启动页概念
> 1. 原生的冷启动页
> 2. material中的home页
## 获取当前视口的宽高
+ 1. MediaQuery.of(context).size.width
+ 2. MediaQuery.of(context).size.height
##  表单部分
>1. 如何调整表单高度,  首先设置 isDense = true, 外面再套一层有高度的container部件
>2. 和Form一起使用时  设置全局的formkey, 通过formkey.currentState调用所有子表单的validator和 onSave方法,  即formkey.currentState.validate() 和 formkey.currentState.save()
>3. 给表单校验提示的文字预留空间 可以设置helperText = '', 这样看起来就不会因为错误提示和是表单布局抖动
## map类
flutter中使用map中的数据 需要person['name']; 一般将json数据转换成类 使用时方便就可以 person.name

## 数据持久化
### SharedPreferences
+ 实例化 SharedPreferences.getInstance()
## 手机权限申请
 + Permission类
 > Permission.storage 存储权限
 > Permission.camera 相机权限
```js
void checkPermission () async {
  // 存储权限
  Permission permission = Permission.storage
  // 权限状态
  PermissionStatus status = await permission.status
  if (status.isUndermined) { // 第一次申请

  } else if (status.isDenied) { // 第一次申请拒绝

  } else if (status.isPermanently) { // 第二次申请拒绝
    
  } else { // 通过

  }
  // 注意 ios中没有第二次申请, 注意兼容性处理
}
```
## 系统级API
### 关闭应用
+ SystemChannels.platform.invokeMethod("SysntemNavigator.pop")
### 获取当前平台
+ Platform
### 当前环境
+ bool.fromEnvironment("dart.vm.product") 判断是否是release环境
## 其它注意点
+ 在initState中是无法访问上下文对象context的 因为widget和state还尚未绑定;可以放在异步队列中执行Future.delayed