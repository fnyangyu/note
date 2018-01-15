# react 笔记

- 用 import 引入 'react' 和 'react-dom'
- jsx语法 注释 用

  ```javascript
   /**/
   //
  ```

- import img from './images/1.jpg' 引入本地图片，然后

  ```javascript
  <img src = {img} alt = '加载失败'　/>
  ```

- jsx语法 需安react插件 apm install react 才能自动补齐

１．组件

- 函数式声明组件，函数名首字母必须大写

  ```javascript
      function() Welcome(){
        return <h1>hello</h1>
      }
      ReactDom.render(<Welcome/>,document.getElementById('root'))
  ```
