# jui
Practical UI for Vue.js

Inspired by [Semantic-ui](http://semantic-ui.com/) and [Element-ui](http://element.eleme.io/)

![image](http://7xnh42.com1.z0.glb.clouddn.com/lamp.png?imageMogr2/thumbnail/640x200>/blur/1x0/quality/75|imageslim)

# 为什么做这个UI

通常，开发Vue.js的项目时，UI框架首选是 饿了么的Element UI。

其中，表单这一块经常用，而Element UI的表单**太繁琐**，这就是出发点。

为了方便使用，最终表单的校验方式同样使用了[async-validator](https://github.com/yiminghe/async-validator)

# 安装

由于`jui`这个名字已经被注册，所以在npm注册的名字是`jim-ui`，

```
npm install jim-ui
```

# 项目规划

第一阶段：完成组件：(2017.11.22已完成)

- `Button 按钮`
- `Input 输入框`
- `Radio 单选框`
- `Checkbox 复选框`
- `Toggle 开关`
- `Form 表单`

第二阶段：完善Form相关的组件，包含：

- `DropDown 选择器`
- `DatePicker 日期选择器`

第三阶段：继续完善其他组件： 

- `Upload 上传`
- `Loading 加载状态`
- `Modal 弹框`

(...未完待续)

# 表单用法

template部分：

```html
<j-form :formData="data" :errorData="error" ref="form" :rules="rules">

  <j-form-item label="账号" prop="name">
    <j-input></j-input>
  </j-form-item>
  
  <j-form-item label="密码" prop="password">
    <j-input type="password"></j-input>
  </j-form-item>
  
  <j-form-item>
    <j-button @click="submit">submit</j-button>
  </j-form-item>
  
</j-form>
```

JavaScript逻辑部分：

```js
export default {
  data() {
    return {
      data: {},
      rules: {},
      error: {}
    }
  },
  methods: {
    submit() {
      this.$refs.form.validate((data) => {
        console.log(data)
      })
    }
  }
}
```

# 组件

### form

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|label-position|标签文本的位置|string|left,right|right|
|error-template|默认的错误模板|string|-|[prop]不能为空
|formData|表单数据|object|-|-|
|rules|验证规则([async-validator](https://github.com/yiminghe/async-validator))|object|-|-|
|errorData|错误信息|object|-|-|

### form-item
 
|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|prop|字段属性|string|-|-|
|label|标签文本|string|-|-|
|type|数据类型|string|-|text|
|required|是否必填|boolean|true,false|true|
|show-message|是否显示错误信息|boolean|true,false|true|
|labelWidth|标签的宽度|string|-|80px|
|contentWidth|内容的宽度|string|-|160px|

### button

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|type|类型|string|-|text|
|plain|朴素风格|boolean|true,false|false|
|disable|不可点击状态|boolean|true,false|false|
|loading|加载状态|boolean|true,false|false|
|nativeType|原生类型|string|-|button|

### input

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|type|类型|string|-|text|
|value|数值|string／number|-|-|
|readonly|是否只读|boolean|true,false|false|
|disable|不可使用状态|boolean|true,false|false|
|loading|加载状态|boolean|true,false|false|
|prefixIcon|前置图标|string|-|-|
|suffixIcon|后置图标|string|-|-|
|placeholder|原生属性|string|-|-|
|name|原生属性|string|-|-|
|max|原生属性|string|-|-|
|min|原生属性|string|-|-|
|step|原生属性|string|-|-|
|autofocus|原生属性|string|-|-|
|form|原生属性|string|-|-|
|disabled|原生属性|string|-|-|
|autoComplete|原生属性|string|-|-|
|focus|获取焦点触发事件|function|-|-|
|blur|失去焦点触发事件|function|-|-|
|change|数值改变时触发事件|function|-|-|

### radio

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|name|原生属性|string|-|-|
|readonly|是否只读|boolean|true,false|false|
|checked|是否已选择|boolean|true,false|false|

### radio-group

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|options|选项|array|-|-|
|value|数值|string／number|-|-|

### checkbox

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|name|原生属性|string|-|-|
|readonly|是否只读|boolean|true,false|false|
|checked|是否已选择|boolean|true,false|false|

### checkbox-group

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|options|选项|array|-|-|
|value|数值|string／number|-|-|

### toggle

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|name|原生属性|string|-|-|
|checked|是否已选择|boolean|true,false|false|

### dropdown

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|name|原生属性|string|-|-|
|options|选项|array|-|-|
|defaultText|默认文案|string|-|请选择|

### loading

|参数|说明|类型|可选值|默认值|
|--|--|--|--|--|
|type|图标类型|string|rotate-plane、sk-circle、sk-fading-circle、double-bounce、rect、cube、bounce|rotate-plane|
|loading|是否正在加载|boolean|true,false|false|
|mask|遮罩|boolean|true,false|true|
|noText|是否显示文案|boolean|true,false|false|
|text|文案|string|-|正在加载...|
