### Vuex
1. **含义**：集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化
2. **使用**：
```
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
```
1. 首先创建一个 store 需要提供一个初始 state(状态) 对象和一些 mutation(突变)
2. 然后可以通过 `store.state` 来获取状态对象，以及`store.commit`  方法触发状态变更
```
store.commit(‘increment’)  // increment 代表的是变化的名字，指定所要的变化，不可直接更改 state，需要通过 mutation 来更改 state
console.log(store.state.count) // -> 1
```