<template>
  <page-container>
    <TextTransition :text="'환영합니다. welcome!!!'"></TextTransition>
    <Album>
      <div slot="0" class="items">0번쨰 슬롯</div>
      <div slot="1" class="items" style="height:400px;">
        <div style="background:yellow;">
          <template v-for="i in 100">
            <div :key="i">dsdsdsdsdsds</div>
          </template>
        </div>
      </div>
      <div slot="2" class="items" style="height:200px;">2번쨰 슬롯</div>
      <div slot="3" class="items" style="height:300px;">3번쨰 슬롯</div>
      <div slot="4" class="items" style="height:400px;">4번쨰 슬롯</div>
      <div slot="5" class="items" style="height:100px;">5번쨰 슬롯</div>
    </Album>
    <!-- <template v-for="i in 200">
      <div :key="i">
        {{ i+'번째 라인!!!' }}
      </div>
    </template> -->
    <nuxt-link to="/find/find-main">
      main gogo
    </nuxt-link>
  </page-container>
</template>

<script>
export default {}
</script>

<style>
.items{
  height:500px;
  background:lightgreen;
  margin:10px;
  overflow-y:auto;
}
</style>
