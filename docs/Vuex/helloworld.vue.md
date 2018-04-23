# 2 helloworld.vue
``` html
<template>
  <div class="hello">
    <div>{{count1}}</div>
    <div>{{count2}}</div>
    <div>{{count3}}</div>
    <button @click="increment()">增加 mapMutations[]</button>
    <button @click="decrement(2)">减少 mapMutations[]</button>
    <button @click="increment2()">增加 mapMutations{}</button>
    <button @click="decrement2(4)">减少 mapMutations{}</button>
    <button @click="increment3()">增加 commit 无参</button>
    <button @click="decrement3_1(4)">减少 commit 有参</button>
    <button @click="decrement3_2(4)">减少 commit 有参(对象)</button>
    <hr>
    <button @click="incrementAsync()">异步增加[]</button>
    <button @click="decrementAsync({amount:5})">异步减少[]</button>    
    <button @click="incrementAsync2()">异步增加{}</button>
    <button @click="incrementAsync3()">异步增加 普通</button>

    <hr>
    <div>{{filterCount4}}</div>
    <div>{{filterCount5}}</div>
    <div>{{filterCount6}}</div>
    <div>{{filterCountCanshu(1)}}</div>
    <div>{{filterCountCanshu2(2)}}</div>
    <div>{{filterCountCanshu3}}</div>
    <hr>
  </div>
</template>


<script>
 
import { mapState, mapMutations, mapGetters, mapActions } from 'vuex';

export default {
  name: 'HelloWorld',
  data() {
    return {

    }
  },
  computed: {
    // ======================== 【 state 】 ================================
    // ===== 【 直接引用 】 =====
    count1() {
      return this.$store.state.count1;
    },
    // ===== 【 mapState[] 】 =====
    ...mapState([
      'count2'
    ]),
    // ===== 【 mapState{} 】 =====
    ...mapState({
      count3: 'count3'
    }),
    // ===== 【 mapGetters[] 】 =====
    ...mapGetters([
      'filterCount4'
    ]),
    // ===== 【 mapGeterrs{} 】 =====
    ...mapGetters({
      filterCount5: 'filterCount5'
    }),
    // ======================== 【 getters 】 ================================
    // ===== 【 直接引用 】 =====
    filterCount6() {
      return this.$store.getters.filterCount6;
    },
    // ===== 【 mapGetters[] canshu 】 =====
    ...mapGetters([
      'filterCountCanshu'
    ]),
    // ===== 【 mapGetters{} canshu 】 =====
    ...mapGetters({
      filterCountCanshu2: 'filterCountCanshu'
    }),
    // ===== 【 直接引用 canshu 】 =====
    filterCountCanshu3() {
      return this.$store.getters.filterCountCanshu(1);
    }
  },
  methods: {
    // ======================== 【 mutations 】 ================================
    // ===== 【 mapMutations[] 】 =====
    ...mapMutations([
      'increment',
      'decrement'
    ]),
    // ===== 【 mapMutations{} 】 =====
    ...mapMutations({
      increment2: 'increment',
      decrement2: 'decrement'
    }),
    increment3: function () {
      return this.$store.commit('increment');
    },
    decrement3_1: function (n) {
      return this.$store.commit('decrement', n);
    },
    decrement3_2: function (n) {
      return this.$store.commit('decrement2', { amount: n });
    },
    // ======================== 【 actions 】 ================================
    ...mapActions([
      'incrementAsync',
      'decrementAsync'
    ]),
    ...mapActions({
      incrementAsync2: 'incrementAsync'
    }),
    incrementAsync3: function () {
      return this.$store.dispatch('incrementAsync');
    }


  }
}
</script>
```
