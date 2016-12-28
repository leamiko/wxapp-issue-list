## 组件
### input 组件

- placeholder 文字重叠
    - *暂无解决方案*
- 获取焦点 和失去焦点时，光标和文字跳动
    - *暂无解决方案*
- 设置居中时，光标出现在奇怪的位置
    - *暂无解决方案*
- bindconfirm 事件在失去焦点时也会触发，类似于 blur
    - *暂无解决方案*
- 对 input 做动画时，如果是获取焦点状态，会失效，因为 input 在获取焦点时是 native 组件，失去焦点后改回 web 组件
    - *暂无解决方案*
- type 为 idcard, digit 时并不是调用数字键盘，目前起作用的只有 number
    - *暂无解决方案*

### scroll-view 组件

- 安卓下列表较长时滚动白屏
    - *目测是渲染性能的问题*
- 动态渲染列表内容的时候，滚动条回到顶部
    - *手动设置 scrollTop 值，组件自己并不会自动更新这个值*

### image 组件

- image 标签的 url 需要添加协议
    - *添加协议头*

## 调试

- 控制台输出错误信息不正确，如 语法错误 等会输出错误指向文件顶部，而不是出错的位置
    - *暂无解决方案*
- 系统错误 `{“baseresponse":{"errcode":-80002,"errmsg”:””}}``
    - *无权限?*
- 某些情况下 wxml 面板空白
    - *暂无解决方案*
- 列表渲染 wx:key 设置不当导致的 $gwx 错误
    - *检查 wx:key 是否配置正确*

## 样式

- nth-child、nth-of-type不支持
    - *单独使用 class 控制*
- inline-block 调试工具 与 真机表现不一致，调试工具有间隔，真机无间隔
    - *设置 font-size:0*
- navigator标签display: flex;失效
    - *暂无解决方案*
- hidden指令值为true时会添加display:none属性，但是权重很低，会被样式中的 display 覆盖
    - *手动设置样式控制*
- background-iamge在真机环境下，无法使用相对路径的图片，base64可以、外链也可以
    - *可以使用 image 组件替代*

## API
- 已拉起的键盘无法收起，`wx.hideKeyboard()` 方法无效
    - *暂无解决方案*
- 快速点击导致页面重复打开
    - *暂无解决方案*
- onReachBottom 重复触发
    - *改用 scroll-view 或者 手动节流*
- Modal 弹窗内容无法换行
    - *自定义弹窗组件*
- wx.request 只支持 UTF8 编码
    - *编码转换*

## 兼容性
- 安卓下目前没有分享
    - *暂无解决方案*
- scroll-view 使用 flex 布局，使用 flex:1 撑起高度时，安卓下 scroll-view 会对下方元素造成不可见的遮挡
    - *可再设置 height: calc(100% - xxx px); 进行兼容*
- 安卓下使用的是 X5 内核，所以很多特性无法使用，比如 Promise、Object.assign、Array.prototype.includes 等等
    - *单独引入 polyfill*

## 其他
- require 只能引入 .js 文件，没有文件后缀或者后缀不是.js 会在最后补上 ‘.js’
    - *暂无解决方案*
- wxml 和 wxss 文件引入文件可以使用绝对路径，以当前应用程序的目录为根目录，js 文件不行
    - *暂无解决方案*
- 模板中出现的某些特殊符号（如 word 中插入的符号）导致模板渲染失败
    - *替换符号 或者 使用变量*
