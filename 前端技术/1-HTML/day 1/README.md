# HTML第一天
## 一.什么是HTML
- Hyper Text Markup Language 超文本标记语言

## 二.HTML的作用
- 写网页，搭建网页基本框架

## 三.开发环境
- vscode+chrome
- [学习网站](https://www.w3school.com.cn)

## 四、标题标签
    <h1>一级标题</h1>最多六级

## 五、表单
	类型：text ，password，radio，select ，checkbox，submit，reset，button,hidden

- text 文本框
```
<!--readonly="true" 为只读,不能够向文本框输入内容-->
 <input type="text" readonly="true">
 <!--placeholder文本框里的提示文字-->
 <input type="text" placeholder="请输入用户名" id="uname"name="uname">
```

- password 密码框
```
密码：<input type="password"id="upsw"name="upsw" placeholder="请输入密码">
```

- radio 单选框
	名字必须相同。checked 为默认关键字
```
性别:<input type="radio"name="sex"value="male">男
    <input type="radio"checked name="sex"value="female">女
```

- select
```
    select 是下拉列表框
    籍贯:<select id="nation"name="nation">
    <option value=#>请选择</option>
    <option value="sc" selected>四川</option>
    <option value=sx>山西</option>
    </select>
```

-  CheckBox是复选框，可以多个选择
```
    爱好：<input type="checkbox"name="love"value="tiqiu">踢球
    <input type="checkbox" checked name="love"value="qixing"> 骑行
    <input type="checkbox"checked   name="love"value="paobu"> 跑步
    <br>
```

- 按钮
   按钮 分为submit，reset，button

  - submit：提交按钮，用于提交表单数据
  - reset 重置
  - button 普通按钮。
```
    <input type="submit" value="注册">
    <input type="reset" value="重置">
    <input type="button" value="普通按钮">
```

### 六、表格
- tr行
- td列
- align文字对齐方式
```
<table>
	<tr>
    	<td align="right">用户名:</td>
    	<td><input type="text"></td>
	</tr>
	<tr>
    	<td align="right">密码:</td>
    	<td><input type="password"></td>
	</tr>
</table>
```

### 七、图片和超链接
- 注：.表示当前目录 ..表示当前目录的上一个目录
```
<a href="http://www.baidu.com">百度</a>
<img alt="没找到" title="科大" src="./images/t.jpg" width="100ps" height="100ps"></a>
<!--alt的文字为没找到时候显示的，是一个碎掉的图片。-->
```
## 八.问题
1. 什么是HTML5？
	HTML5是HTML最新的修订版本，2014年10月由万维网联盟（W3C）完成标准制定。
2. HTML网页文件是以什么后缀名结尾的？
	.htm 或者 .HTML
3. HTML5的前一个版本是什么？
	HTML4.01
4. HTML4与HTML5的区别？
  - 定义不同
  	&emsp;&emsp;HTML5是超文本标记语言的第五次修改，HTML4是为了适应pc时代产生的，HTML5是为了适应移动互联网产生的。他们都是w3c(World Wide Web)万维网推荐的标准语言。
  - 声明不同
    HTML4:
    ```
    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
        "http://www.w3.org/TR/html4/loose.dtd">
    ```
    HTML5:
    ```
    <!DOCTYPE html>
    ```
  - 标签的区别
    &emsp;&emsp;HTML5相比HTML4代码更加简洁，HTML5的一些新元素、新属性等可以使web开发变的容易简单，比如说HTML5提高了API。HTML5之前有很多功能必须依靠javascript实现，现在使用HTML5元素的标签属性就可以。由于HTML5在web页面这种大量可代替脚本（javascript）属性使语言变的简单易懂，而仅靠html4需要和javascript配合才能做到。
  - HTML5增加了新的元素
    &emsp;&emsp;HTML5增加了canvas 元素（绘画）、video 元素（媒体回放）、audio 元素、新的特殊内容元素（article、footer、header、nav、section）、表单控件（calendar、date、time、email、url、search），比如之前用div现在可以用HTML5结构化标签代替，这样使整个页面更加直观，容易理解。
  - HTML5更适应时代的要求
    &emsp;&emsp;移动互联网时代相比pc时代更加迫切希望有一个统一的标准。之前由于各个浏览器不统一，因为修改浏览器兼容引起的bug浪费了大量的时间。在HTML5中视频、音频、图像、动画都会标准化，会解决浏览器兼容这个令人头疼的问题。
5. post和get的区别? https://www.w3school.com.cn/tags/html_ref_httpmethods.asp
	- 表单数据是否在地址栏中显示
	- 隐藏表单：用于网页之间传递数据，不用于敏感数据传递。
