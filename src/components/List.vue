<template>
<div id="app" class="container">
    <p class="col-md-12">
        <!-- 버튼테두리 없음 -->
        <b-button v-on:click="ListToggle">리스트팝업토글</b-button>
    </p>
  <div class="row">
    <ul v-if="리스트토글">
      <li v-for="(a, index) in 리스트" :key="index">
        <a href="">{{a}}</a>
      </li>
    </ul>
  </div>

  <div class="row">
      <Card class="col-md-6" v-for="(제품, i) of 기본제품들" :key="i + 제품" v-bind:제품데이터="제품">
      </Card>
  </div>

</div>


</template>

<script>
import Data from "../data/data";
import Card from '@/components/Card.vue';

export default {
    components:{
        Card,
    },
    // name : 'Card',
    data() {
        return {
        리스트: [ '리셋', '50만원 미만', '고가순', '저가순'],
        리스트토글 : false,
        기본제품들 : Data, //원본데이터
        제품들 : [...Data] //임포트한 데이터 반복
        }
    },
    methods: {
        ListToggle(){
        this.리스트토글 = !this.리스트토글;
        }
    },

}
</script>

<style>

</style>