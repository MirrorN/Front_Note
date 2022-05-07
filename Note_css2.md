### Note

#### Emmet语法

使用缩写，提高 html/css 的编写速度，vscode 已经集成

- 快速生成 HTML 结构语法
- 快速生成 CSS 样式语法

##### 1.快速生成 HTML 结构语法

- 生成标签：**直接输入标签名按tab键**

- 生成多个相同标签：标签名加*号，例如:

  ```
  div*4
  // 中间不要有空格
  ```

   

- 父子关系，直接使用`>`表示：

  ```
  ul>li
  
  生成结果：
  <ul>
    <li></li>
  </ul>
  
  div>span ...
  ```

- 兄弟关系的标签，直接使用`+`号

  ```
  div+p
  
  生成结果：
  <div></div>
  <p></p>
  ```

- 生成带有类名以及ID名的，直接`.class`或者`#id`

  ```
  div.class:
  <div class="class"></div>
  
  div#id:
  <div id="id"></div>
  ```

- 如果生成的 div 类名是有顺序的，可以使用自增符号 `$`:

  ```
  //生成两个div：
  div.cls$*2
  
  生成效果：
  <div class="cls1"></div>
  <div class="cls2"></div>
  ```

- 如果标签内默认有文字：

  ```
  div{3333}
  生成结果：
  <div>333</div>
  
  div{333}.demo$*2
  生成结果：
  <div class="demo1">333</div>
  <div class="demo2">333</div>
  
  
  div{$}*2:
  <div>1</div>
  <div>2</div>
  ```

  

##### 2.快速生成CSS样式

基本采取简写形式：（多个单词的时候，每个单词的首字母）

```
w200 -> width: 200px
lh 26 -> line-height: 26px
```



#### 快速格式化代码

vscode “格式化文档”， `Alt+shift+F`

1. 首选项

2. 在“用户区”搜索 "emmit.include"

3. 找到 Emmet: Include Languages

4. 修改json文件或者“添加项”

   ```
   editor.formatOnType: true,
   editor.formatOnSave: true
   ```

**上述为旧版本方法**

新版本VScode直接搜索 `format`

在`文本编辑器`中找到`Editor: Format On Save`，勾选即可



#### 复合选择器

基本选择器组合形成

- 后代选择器
- 子选择器
- 并集选择器
- 伪类选择器



##### 1.后代选择器（重要）

选择父元素中的子元素





##### 2.子元素选择器