<template>
  <b-container class="bv-example-row">
    <b-row class="text-center">

      <b-col md="2">
        <b-button v-on:click="ListToggle">리스트팝업토글</b-button>

        <p class="col-md-12"><b-button variant="outline-dark" v-on:click="resetData">전체보기</b-button></p>
        <p class="col-md-12"><b-button variant="outline-dark" @click="sortLimitHalfMillion">50만원미만</b-button></p>
        <p class="col-md-12"><b-button variant="outline-dark" @click="sortDesc">고가순</b-button></p>
        <p class="col-md-12"><b-button variant="outline-dark" @click="sortAsce">저가순</b-button></p>

        <!-- <div class="row"> -->
          <ul v-if="리스트토글">
            <li v-for="(a, index) in 리스트" :key="index">
              <a href="">{{a}}</a>
            </li>
          </ul>
        <!-- </div> -->
      </b-col>

      <b-col cols="9" md="10">

    <div class="row">
      <!-- col-md-6으로 양옆배치 -->
        <Card class="col-md-6" v-for="(제품, i) of 제품들" :key="i + 제품" v-bind:제품데이터="제품">
        </Card>
    </div>
      </b-col>
    </b-row>

  <b-row class="text-center">
    <b-col>1 of 3</b-col>
    <b-col cols="5">2 of 3 (wider)</b-col>
    <b-col>3 of 3</b-col>
  </b-row>
</b-container>



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
        제품들 : [...Data], //원본데이터 카피
        초기 : [...Data], //초기화를 위한 데이터 카피
        }
    },
    methods: {
        ListToggle(){
        this.리스트토글 = !this.리스트토글;
        },

        // ※filter, sort 메소드 : 원본데이터 변형 가져옴

        //50만원 미만
        sortLimitHalfMillion :function(){
          this.resetData();
          this.제품들 = this.기본제품들.filter(function(data){
            return data.price < 500000;
          });
        },

        //고가순
        sortDesc(){
          //sort() : 배열안의 원소 정렬
          this.제품들 = this.기본제품들;
          // this.resetData();//이거쓰면 작동xxxx
          this.제품들.sort(function(a,b){
            return b.price - a.price; //내림차순
          });
        },

        //저가순
        sortAsce : function(){
          this.제품들 = this.기본제품들;
          // this.resetData();
          this.제품들.sort(function(a,b){
            return a.price - b.price; //오름차순
          });
        },

        //리스트 리셋
        resetData(){
          /////이거 다 안됨!!!! ★
          // this.제품들 = [...Data];
          // this.제품들 = Data;
          // this.제품들 = this.기본제품들;
          this.제품들 = this.초기;
        },
    },

}
</script>

<style>
Card {
  border: 1px solid black;
}
div{
  border: 1px solid black;

}
</style>