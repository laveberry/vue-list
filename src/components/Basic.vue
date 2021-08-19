<template>
  <div>
    <p v-if="isMonday">{{안녕}}</p>
    <span v-for="이름 in 이름들" v-bind:key="이름">{{이름}}</span>

    <div v-for="(사람, i) in 사람들" :key="i">
      <!-- 보이기/숨기기위한 설정 -->
      <div v-if="isMonday">
        <h2>{{사람.이름}}</h2>
        <p>{{사람.나이}}</p>
      </div>
    </div>

    <!-- 이벤트리스너 -->
    <button v-on:click="hello">클릭하면 알립창이 뜹니다</button> <br>
    <button @click="checkClick">
      <!-- if문 설정, 다른방법 있나 알아보기 -->
      <span v-if="isMonday==true">클릭시 안보임</span>
      <span v-if="isMonday==false">클릭시 반복보임</span>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      안녕 : '안녕하세요',
      isMonday : false,
      이름들 : ['아이유','태연','수지','서강준','이진욱'],
      사람들 : [
        {
          이름 : '아이유',
          나이 : '29살'
        },
        {
          이름 : '태연',
          나이 : '33살'
        },
        {
          이름 : '서강준',
          나이 : '27살'
        },
        {
          이름 : '이진욱',
          나이 : '35살'
        },
      ]

    }
  },
  //이벤트리스너
  methods: {
    hello : function(){
      alert('hello!');
    },
    checkClick : function(){
      this.isMonday = !this.isMonday
    }
  },
  

}
</script>

<style>

</style>
