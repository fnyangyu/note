

# https://codesandbox.io/s/jolwj35vv

# https://reactcommunity.org/react-transition-group/

```js
import React, { Component } from 'react'
import { render } from 'react-dom'
import styled from 'styled-components'
import bgImg from './assets/bg.png'
import heart from './assets/heart.png'
import { CSSTransition } from 'react-transition-group'

class App extends Component {
  state = {
    show: false
  }

  handleClick = e => {
    e.preventDefault()
    this.setState({
      show: true
    })
    setTimeout(
      () => {
        this.setState({
          show: false
        })
      },
      1000
    )
  }

  render() {
    const { show } = this.state
    return (
      <Wrap>
        <Button onClick={this.handleClick}>Click Me</Button>
        <CSSTransition in={show} timeout={1000} classNames='like'>
          <div className='likes-heart'>88</div>
        </CSSTransition>
      </Wrap>
    )
  }
}

const Wrap = styled.div`
  background-image: url(${bgImg});
  height: 100vh;

  .likes-heart {
    background: url(${heart}) center no-repeat;
    background-size: contain;
    font-size: 30px;
    padding: 30px;
    position: absolute;
    top: 50%;
    left: 50%;
    color: #ff4081;
    transform: translateX(-50%) translateY(-50%) scale(1);
    opacity: 0;
    transition: all 0.5s;
  }

  .like-enter.likes-heart {
    opacity: 1;
    transform: translateX(-50%) translateY(-50%) scale(5);
  }
`

const Button = styled.button`
  width: 250px;
  height: 70px;
  background: #00bcd4;
  color: white;
`

render(<App />, document.getElementById('root'))

```


# 使用 css-transition-group
先来看看要做出的效果。

# 创建项目
create-react-app episode-241-demo
进入项目删除整个 src 文件夹

rm -rf src
创建 src/index.js

```js
import React, { Component } from 'react'
import { render } from 'react-dom'

class App extends Component {
  render() {
    return (
      <div>
        App
      </div>
    )
  }
}

render(<App />, document.getElementById('root'))
```
运行 npm start 启动。

浏览器中，可以看 App 字符串。

# 安装 styled-components
npm i styled-components
虽然直接添加 css 文件也是一样能完成功能，但是这里还是来安装一下 styled-components ，以便把 css 作用域控制到组件局部。

找一张颜色比较深的图标做背景。

wget http://o86bpj665.bkt.clouddn.com/posters/meteor-react-bird.png
把图片放到项目的 src/assets 文件夹下，命名为 bg.png 。

```js
// src/index.js

import bgImg from './assets/bg.png'
import styled from 'styled-components'

    return (
      <Wrap>
        App
      </Wrap>
    )

const Wrap = styled.div`
  background-image: url(${bgImg});
  height: 100vh;
`
```

导入图片，导入 styled，把 div 改为样式组件 Wrap ，然后定义样式组件 Wrap ，把图片作为 Wrap 的背景图。让 Wrap 沾满整个屏幕区域。

# 添加一个大大的 Button 进来
```js
    <Wrap>
      <Button>Click Me</Button>
      App
    </Wrap>

const Button = styled.button`
  width: 250px;
  height: 70px;
  background: #00bcd4;
  color: white;
`
```

添加样式组件 Button ，显示 Click Me ，下面定义 Button ，设置一个比较大的宽高和项目的背景色。

# 安装 React 的 transition 插件
npm install react-transition-group
版本是比较混乱的，官方版已经不维护，社区1.0版跟官方版兼容，我这里安装的是社区2.0版，也是最新版。

所以看文档的时候也不要看官方的这篇 了，而要看这篇 。

```js
import { CSSTransition } from 'react-transition-group'

class App extends Component {
  state = {
    show: false
  }

  handleClick = e => {
    e.preventDefault()
    this.setState({
      show: !this.state.show
    })
  }

  render() {
    const { show } = this.state
    return (
      <Wrap>
        <Button onClick={this.handleClick}>Click Me</Button>
        <CSSTransition in={show} timeout={10000} classNames='like'>
          <div className='likes-heart'>88</div>
        </CSSTransition>
      </Wrap>
    )
  }
}
```

1. 导入 CSSTransition ，下面按照一个组件的形式来使用 CSSTransition ，可以传入 in 属性，来控制 CSSTranstion 的进入和退出，这里用一个状态值 show 来控制，然后 timeout 来控制失效时间，这里设置为10秒，classNames 注意，不是单数的 className 设置成 like ，这个是任意的，我们这里要实现点赞功能所以叫 like 。接下来包裹到其中的是一个 div className 叫 likes-heart 是一个显示点赞数量的爱心形图案。显示88个赞。

2. 状态值 show ，要是一个可以改变的布尔型。先来添加初始值，然后 handleClick 中可以来回改变它的 true 和 false 。

3. handleClick 的触发是通过按钮的 onClick 事件。

4. 浏览器中，当我第一次点按钮的时候 show 会由 false 变成 true , 也就是 CSSTransition 的 in 属性的值由 false 变成 true 。导致的结果是 class 名为 likes-heart 的 div ，会被先添加 like-enter 的这个 class 名，这个 class 名中的 like 就是来自于我们给 CSSTranstion 组件设置的那个 classNames 属性。然后下一个眼睛不可分辨的时间后，又添加了一个 like-enter-active class 名。这样，div 的状态其实就经历了两次切换，可以在任意一个设置过渡效果。

5. 当然，like-enter 和 like-enter-active 不会一直都在，再经历了 timeout 属性指定的时间后，它们就会消失。也就是 div 的 class 名又会经历反向的切换，过程中也可以去显示过渡效果。

6. 然后再点按钮，show 由 true 又变成 false 。这次达成的效果其实跟初次点按钮的时候比较类似，div 状态值首先是 likes-heart ，然后变成两个 likes-heart 和 like-enter ，最后变成三个，也就是前两个加上 like-enter-active ，也是两次切换，也是经过了 timeout 指定的时间后，like-enter 和 like-enter-active 都会消失。

7. 设置爱心样式
先来完成 likes-heart 这个 div 的默认样式

```js
import heart from './assets/heart.png'

const Wrap = styled.div`

  .likes-heart {
    background: url(${heart}) center no-repeat;
    background-size: contain;
    font-size: 30px;
    padding: 30px;
    position: absolute;
    top: 50%;
    left: 50%;
    color: #ff4081;
    transform: translateX(-50%) translateY(-50%) scale(1);
  }
`
```

8. 下载爱心图片，放到 assets/ 文件夹，导入。通过设置背景的方式来使用图片。设置字体样式，通过 postion absolute 然后 top left 都是50这种形式，可以让 likes-heart 的左上角在页面上处于中心点位置。然后通过 transoform 的 translateX 设置，就可以真正的让爱心居中了。

9. 过渡效果
```js
  .likes-heart {
    transform: translateX(-50%) translateY(-50%) scale(1);
    opacity: 0;
    transition: all 1s;
  }

  .like-enter.likes-heart {
    opacity: 1;
    transform: translateX(-50%) translateY(-50%) scale(5);
  }
```

这样 show 变成 true 的过程中就会显示过渡了。

控制退出
把 show 要设置成 false ，不然下次点按钮就不能触发爱心显示了。
