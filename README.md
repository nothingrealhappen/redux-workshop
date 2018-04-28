# redux-workshop
-------

# 为什么需要 Redux
![you might not need redux](http://blog.isquaredsoftware.com/presentations/2018-03-redux-fundamentals/static/media/you-might-not-need-redux.6ed95d25.png)

## 有什么问题
### jQuery 与 React 之间的交互
https://codesandbox.io/s/0my672voxn

### 跨多个组件的状态共享

```
App
  ProductHouse  (updateHouseSelection price)
    Total
  ProductCar    (updateCarSelection price)
    Total
  SummaryPage   (subscribeProductChange)
    ProductDetails
    Total
```

#### 需要都组织到 App 这个级别的组件吗？扩展性？
#### 触发一次 Product 价格的更新用什么方法？
`this.props.updateProduct({ name: 'car', price: 0 })`

#### 计算 productTotal 的逻辑代码如何复用

```
const total = _.sumBy(state.product, 'price');
```
这段代码应该放在每个 `<Total />` 组件中吗

#### 如果整个应用的数据需要被客户端存储起来呢？(localStore)
这部分存储逻辑写在哪？是否需要集中管理数据？如果数据分散在许多个 container 组件中，如何做到存储整个应用的数据？

## 数据越来越多且越来越复杂，你需要一个集中管理数据的方案，保证你的 View 更加地轻量，反馈交互/渲染页面 react(data) => page

# 什么是 Redux

# 语重心长的总结

## Well Redux is just a pattern

```
import React, { Component } from 'react';

const counter = (state = { value: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { value: state.value + 1 };
    case 'DECREMENT':
      return { value: state.value - 1 };
    default:
      return state;
  }
}

class Counter extends Component {
  state = counter(undefined, {});
  
  dispatch(action) {
    this.setState(prevState => counter(prevState, action));
  }

  increment = () => {
    this.dispatch({ type: 'INCREMENT' });
  };

  decrement = () => {
    this.dispatch({ type: 'DECREMENT' });
  };
  
  render() {
    return (
      <div>
        {this.state.value}
        <button onClick={this.increment}>+</button>
        <button onClick={this.decrement}>-</button>
      </div>
    )
  }
}
```

# what is dataStore