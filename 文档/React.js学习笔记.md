# React.js学习笔记

## 一. HTMl模版

```
<!DOCTYPE html>
<html>
  <head>
    <script src="../build/react.js"></script>
    <script src="../build/react-dom.js"></script>
    <script src="../build/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    //<script> 标签的 type 属性为 text/babel,React 独有的 JSX 语法，跟 JavaScript 不兼容
    <script type="text/babel">
      // ** Our code goes here! **
    </script>
  </body>
</html>
```

## 二.ReactDOM.render()