<template>
  <div>
    <p v-if="isMonday">{{안녕}}</p>
    <p v-for="이름 in 이름들" v-bind:key="이름">{{이름}}</p>
    <p></p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      이름들 : ['아이유','태연','수지','서강준','이진욱'],
      안녕 : '안녕하세요',
      isMonday : false
    }
  },
}
</script>

<style>

</style>
