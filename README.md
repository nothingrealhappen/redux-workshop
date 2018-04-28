# redux-workshop
-------

# 为什么需要 Redux
![you might not need redux](http://blog.isquaredsoftware.com/presentations/2018-03-redux-fundamentals/static/media/you-might-not-need-redux.6ed95d25.png)

## 有什么问题
### jQuery 与 React 之间的交互
https://codesandbox.io/s/0my672voxn

# 什么是 Redux
## Redux Principles

### 单一数据源
![6024ef30-312a-4c7c-bfd2-eb72fba097ef](md/6024ef30-312a-4c7c-bfd2-eb72fba097ef.png)
### state是只读的

### 通过纯函数派生state
![1_wLRhZ0wtI0duLsigdxL1CA](md/1_wLRhZ0wtI0duLsigdxL1CA.png)

## 基本概念
### Actions
1. Action是一个Plain Object
2. Action必须声明type

```js
const ADD_TODO = 'ADD_TODO'

const action = {
  type: ADD_TODO,
  text: 'Build my first Redux app'
}
```
### Reducers
Reducer是一个纯函数
Reducer对于不同的Action进行响应

```js
(previousState, action) => newState
```

#### Never Do
1. Mutate its arguments;
2. Perform side effects like API calls and routing transitions;
3. Call non-pure functions, e.g. Date.now() or Math.random().


### Store
+ 保存应用状态的仓库

+ 通过 `getState()` 访问;

+ 通过 `dispatch(action)` 更新我们的state;

+ 通过 `subscribe(listener)` 来响应store的变化;


## 数据流动
![redux-data-flow-with-angular-2-19-638](md/redux-data-flow-with-angular-2-19-638.jpg)
## 和React配合使用
### Presentation & Container
 ![container-and-presentational](md/container-and-presentational.jpg)

### React-Redux

1. Provider

Provider提供Store的注入

2. Connect(mapStateToProps, mapDispatchToProps)

将React组件接入Store

3. mapStateToProps

store.getState()的语法糖

4. mapDispatchToProps

store.dispatch()的语法糖


# 语重心长的总结

## Well Redux is just a pattern

# what is dataStore

