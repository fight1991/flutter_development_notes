# flutter_development_notes
flutter开发笔记
## 表单部分
>1. 如何调整表单高度,  首先设置 isDense = true, 外面再套一层有高度的container部件
>2. 和Form一起使用时  设置全局的formkey, 通过formkey.currentState调用所有子表单的validator和 onSave方法,  即formkey.currentState.validate() 和 formkey.currentState.save()
>3. 给表单校验提示的文字预留空间 可以设置helperText = '', 这样看起来就不会因为错误提示和是表单布局抖动
## 其他
flutter中使用map中的数据 需要person['name']; 一般将json数据转换成类 使用时方便就可以 person.name
