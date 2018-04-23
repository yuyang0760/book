# 1 index.js
```javascript
import Vue from 'vue';
import vuex from 'vuex';
Vue.use(vuex);

export default new vuex.Store({
    state: {
        count1: 1,
        count2: 2,
        count3: 3,
        count4: [
            { id: 1, name: "yy", age: 18, show: true },
            { id: 2, name: 'lh', age: 18, show: true }
        ]
    },
    mutations: {
        increment: function (state) {
            state.count1++;
        },
        // increment: function (state,n) {
        //     state.count1+=n;
        // },
        // decrement: function (state, n) {
        //     state.count1 -= n;
        // },
        decrement: (state, n) => { state.count1 -= n },
        // decrement2: function (state, { amount }) {
        //     state.count1 -= amount;
        // }
        decrement2: (state, { amount }) => { state.count1 -= amount }
    },
    getters: {
        filterCount4: function (state) {
            return state.count4.filter((s) => s.show);
        },
        filterCount5: function (state) {
            return state.count4.filter((s) => s.show);
        },
        // filterCount6: function (state) {
        //     return state.count4.filter((s) => s.show);
        // },
        filterCount6: state => state.count4.filter((s) => s.show),

        // filterCountCanshu: function (state) {
        //     return function (id) {
        //         return state.count4.filter((s) => s.id === id);
        //     }
        // }
        filterCountCanshu: state => id => state.count4.filter((s) => s.id === id)
    },
    actions: {
        incrementAsync({ commit }) {
            setTimeout(() => {
                commit('increment');
            }, 1000);
        },
        decrementAsync({ commit }, de) {
            setTimeout(() => {
                commit('decrement', de.amount);
            }, 1000);
        }
    }
 

})
```
